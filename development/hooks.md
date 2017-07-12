# Hooks

## Create a Hook
To create a hook, you need:
- to create a file `custom/Espo/Custom/Hooks/{EntityName}/{HookName}.php`;
- to declare hook type action;
- Clear Cache in Administartion.

## Hook Types

The main hook types are:

- beforeSave
- afterSave
- beforeRemove
- afterRemove
- afterRelate
- afterUnrelate
- afterMassRelate

### New Hook Type
You can use own one hook type and trigger it with

`$this->getEntityManager()->getHookManager()->process($entityType, $hookType, $entity, $options);`

## Hook Order
If you have several hooks, related to one Entity Type and with the same hook type, and order of running is important, you can set a `public static $order` property in integer value

Ascending order - the hook with the smallest order number runs first.

## _Example_
This example set Account Name for new Leads, if it is not set.

`custom/Espo/Custom/Hooks/Lead/AccountName.php`

```
namespace Espo\Custom\Hooks\Lead;

use Espo\ORM\Entity;

class AccountName extends \Espo\Core\Hooks\Base
{    
    public function beforeSave(Entity $entity, array $options = array())
    {
        if($entity->isNew() && !$entity->get('accountName')) { 
            $entity->set("accountName","No Account");
	   }
    }
}
```