---
title: Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Użyj koncepcji seedwork jako punkt wyjścia, aby rozpocząć implementację dla modelu domeny zorientowanych na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: ab0aadc28dbd1175c75b04dadca29b7b0947f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116569"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)

Folder rozwiązania zawiera folder *SeedWork.* Ten folder zawiera niestandardowe klasy podstawowe, których można używać jako podstawy dla jednostek domeny i obiektów wartości. Użyj tych klas podstawowych, aby nie mieć nadmiarowego kodu w klasie obiektów każdej domeny. Folder dla tych typów klas nosi nazwę *SeedWork,* a nie coś w *rodzaju Framework*. Nazywa *seedwork,* ponieważ folder zawiera tylko mały podzbiór klas wielokrotnego użytku, które naprawdę nie można uznać za framework. *Seedwork* to termin wprowadzony przez [Michaela Feathersa](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) i spopularyzowany przez [Martina Fowlera,](https://martinfowler.com/bliki/Seedwork.html) ale możesz również nazwać ten folder Common, SharedKernel lub podobnym.

Rysunek 7-12 przedstawia klasy, które tworzą seedwork modelu domeny w mikrousługi porządkowania. Ma kilka niestandardowych klas podstawowych, takich jak Entity, ValueObject i Wyliczenie, a także kilka interfejsów. Te interfejsy (IRepository i IUnitOfWork) informują warstwę infrastruktury o tym, co należy zaimplementować. Te interfejsy są również używane za pośrednictwem iniekcji zależności z warstwy aplikacji.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Zrzut ekranu przedstawiający klasy zawarte w folderze SeedWork.":::
Szczegółowa zawartość folderu SeedWork, zawierająca klasy podstawowe i interfejsy: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs i ValueObject.cs.
:::image-end:::

**Rysunek 7-12**. Przykładowy zestaw klas podstawowych i interfejsów modelu domeny "seedwork"

Jest to typ ponownego użycia kopii i wklejania, który wielu deweloperów współużytkuje między projektami, a nie formalne ramy. Prace seedworks można mieć w dowolnej warstwie lub bibliotece. Jeśli jednak zestaw klas i interfejsów jest wystarczająco duży, można utworzyć bibliotekę pojedynczej klasy.

## <a name="the-custom-entity-base-class"></a>Niestandardowa klasa podstawowa jednostki

Poniższy kod jest przykładem klasy podstawowej jednostki, gdzie można umieścić kod, który może być używany w ten sam sposób przez dowolną jednostkę domeny, takich jak identyfikator jednostki, [operatory równości,](../../../csharp/language-reference/operators/equality-operators.md)lista zdarzeń domeny na jednostkę itp.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;
    private List<INotification> _domainEvents;
    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public List<INotification> DomainEvents => _domainEvents;
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() ^ 31;
            // XOR for random distribution. See:
            // https://docs.microsoft.com/archive/blogs/ericlippert/guidelines-and-rules-for-gethashcode
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null));
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

Poprzedni kod przy użyciu listy zdarzeń domeny na jednostkę zostanie wyjaśniony w następnych sekcjach podczas koncentrowania się na zdarzeniach domeny.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty repozytorium (interfejsy) w warstwie modelu domeny

Kontrakty repozytorium są po prostu interfejsy .NET, które wyrażają wymagania umowy repozytoriów, które mają być używane dla każdego agregacji.

Same repozytoria z kodem EF Core lub innymi zależnościami i kodem infrastruktury (Linq, SQL itp.) nie mogą być implementowane w modelu domeny; repozytoria powinny implementować tylko interfejsy zdefiniowane w modelu domeny.

Wzorzec związany z tą praktyką (umieszczenie interfejsów repozytorium w warstwie modelu domeny) jest wzorzec oddzielone interfejsu. Jak [wyjaśnił](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, "Użyj oddzielonego interfejsu, aby zdefiniować interfejs w jednym pakiecie, ale zaimplementuj go w innym. W ten sposób klient, który potrzebuje zależności od interfejsu, może być całkowicie nieświadomy implementacji."

Po wzorzec oddzielone interfejsu umożliwia warstwy aplikacji (w tym przypadku projektu interfejsu API sieci Web dla mikrousługi) mieć zależność od wymagań zdefiniowanych w modelu domeny, ale nie bezpośrednią zależność od warstwy infrastruktury/trwałości. Ponadto można użyć funkcji Iniekcji zależności do izolowania implementacji, która jest implementowana w warstwie infrastruktury/trwałości przy użyciu repozytoriów.

Na przykład w poniższym przykładzie z interfejsem IOrderRepository definiuje, jakie operacje klasa OrderRepository będzie musiała zaimplementować w warstwie infrastruktury. W bieżącej implementacji aplikacji kod po prostu musi dodać lub zaktualizować zamówienia do bazy danych, ponieważ zapytania są dzielone zgodnie z uproszczonym podejściem CQRS.

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);

    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. Oddzielone interfejs.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Poprzedni](net-core-microservice-domain-model.md)
>[następny](implement-value-objects.md)
