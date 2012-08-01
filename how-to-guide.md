1.Cache & Log fix
--------------------
rm -rf app/cache/*
rm -rf app/logs/*
sudo chmod +a "_www allow delete,write,append,file_inherit,directory_inherit" app/cache app/logs
sudo chmod +a "lukaszroth allow delete,write,append,file_inherit,directory_inherit" app/cache app/logs

2.Mapping from database
--------------------------
Do it once at the beginning. Generated entities overwriting every local changes.

php app/console doctrine:mapping:convert yml ./src/Frnsh/AdminBundle/Resources/config/doctrine/metadata/orm --from-database --filter="Magazine"  --force
php app/console doctrine:mapping:import FrnshAdminBundle annotation
php app/console doctrine:generate:entities FrnshAdminBundle

3.CRUD
-----------------
php app/console generate:doctrine:crud --entity=FrnshAdminBundle:Magazine --format=annotation --with-write --no-interaction
php app/console generate:doctrine:crud --entity=FrnshAdminBundle:Article --format=annotation --with-write --no-interaction
php app/console generate:doctrine:crud --entity=FrnshAdminBundle:ArticleComment --format=annotation --with-write --no-interaction

4.Fixtures
---------------
php app/console doctrine:fixtures:load

5.Entity Manager functions with arguments
----------------------------
public function find($id, $lockMode = LockMode::NONE, $lockVersion = null)
public function findAll()
public function findBy(array $criteria, array $orderBy = null, $limit = null, $offset = null)
public function findOneBy(array $criteria)

6.Entity extended class annotation  (prevent to create db table with the name of new class)
----------------------------

/**
 * @Orm\MappedSuperclass
 * @ORM\Table(name="user")
 */


7.Update db schema based on the entity changes
----------------------------
php app/console doctrine:schema:update --dump-sql    #show sql dump
php app/console doctrine:schema:update --force       #force update db

8.Load fixtures if db is not empty
---------------------------
php app/console doctrine:schema:drop --force --full-database
php app/console doctrine:schema:update --force
php app/console doctrine:fixtures:load

9.Doctrine @HasLifecycleCallbacks
-----------------------------------
@PostLoad, @PrePersist, @PostPersist, @PreRemove, @PostRemove, @PreUpdate, @PostUpdate

Usage:

/**
 * @ORM\prePersist
 */
public function setCreatedValue()
{
    $this->created = new \DateTime();
}

10.Generate entity for selected bundle
----------------------------------------
php app/console doctrine:generate:entities FrnshUserBundle:Conversation

11.Switch user in dev project on the fly from url
----------------------------------------
app_dev.php?_switch_user=admin
exit from switched user
app_dev.php?_switch_user=_exit

12. Foreight keys
_____________________
SET FOREIGN_KEY_CHECKS = 0;
SET FOREIGN_KEY_CHECKS = 1;

SET FOREIGN_KEY_CHECKS = 0;
delete from ord;
delete from ord_product;
delete from ord_address;
delete from ord_card;
SET FOREIGN_KEY_CHECKS = 1;


