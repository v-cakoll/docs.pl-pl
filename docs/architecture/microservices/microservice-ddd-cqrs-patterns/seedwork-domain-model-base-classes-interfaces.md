---
title: Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Użyj koncepcji seedwork jako punkt wyjścia do rozpoczęcia implementacji dla modelu domeny zorientowanej na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 545be2723ba468a5fd65f81978799328234ca113
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988313"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)

Folder rozwiązania zawiera folder *SeedWork.* Ten folder zawiera niestandardowe klasy podstawowe, których można używać jako bazy dla encji domeny i obiektów wartości. Użyj tych klas podstawowych, aby nie mieć nadmiarowego kodu w klasie obiektów każdej domeny. Folder dla tych typów klas nazywa *seedwork,* a nie coś *framework*. Nazywa się *SeedWork,* ponieważ folder zawiera tylko mały podzbiór klas wielokrotnegoużytnia, które naprawdę nie mogą być uważane za framework. *Seedwork* to termin wprowadzony przez [Michaela Feathersa](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) i spopularyzowany przez [Martina Fowlera,](https://martinfowler.com/bliki/Seedwork.html) ale można również nazwać ten folder Common, SharedKernel lub podobny.

Rysunek 7-12 przedstawia klasy, które tworzą seedwork modelu domeny w mikrousługi zamawiania. Ma kilka niestandardowych klas podstawowych, takich jak Entity, ValueObject i Wyliczanie, a także kilka interfejsów. Te interfejsy (IRepository i IUnitOfWork) informują warstwę infrastruktury o tym, co należy zaimplementować. Te interfejsy są również używane za pośrednictwem iniekcji zależności z warstwy aplikacji.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Zrzut ekranu przedstawiający klasy zawarte w folderze SeedWork.":::
Szczegółowa zawartość folderu SeedWork zawierająca klasy podstawowe i interfejsy: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs i ValueObject.cs.
:::image-end:::

**Rysunek 7-12**. Przykładowy zestaw klas podstawowych i interfejsów modelu domeny "seedwork"

Jest to typ ponownego użycia kopiowania i wklejać, które wielu deweloperów współużytkuje między projektami, a nie formalnej struktury. W dowolnej warstwie lub bibliotece można mieć materiały źródłowe. Jednak jeśli zestaw klas i interfejsów staje się wystarczająco duży, można utworzyć bibliotekę pojedynczych klas.

## <a name="the-custom-entity-base-class"></a>Niestandardowa klasa podstawowa encji

Poniższy kod jest przykładem klasy podstawowej jednostki, w której można umieścić kod, który może być używany w ten sam sposób przez dowolną encję domeny, taką jak identyfikator jednostki, [operatory równości,](../../../csharp/language-reference/operators/equality-operators.md)lista zdarzeń domeny dla każdej jednostki itp.

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

Poprzedni kod przy użyciu listy zdarzeń domeny na jednostkę zostaną wyjaśnione w następnych sekcjach podczas koncentrowania się na zdarzeniach domeny.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty repozytorium (interfejsy) w warstwie modelu domeny

Kontrakty repozytorium są po prostu interfejsy .NET, które wyrażają wymagania umowy repozytoriów, które mają być używane dla każdego agregacji.

Repozytoria się, z kodu EF Core lub innych zależności infrastruktury i kodu (Linq, SQL, itp.), nie mogą być implementowane w modelu domeny; repozytoria powinny implementować tylko interfejsy zdefiniowane w modelu domeny.

Wzorzec związany z tą praktyką (umieszczanie interfejsów repozytorium w warstwie modelu domeny) jest wzorcem interfejsu oddzielonego. Jak [wyjaśnił](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, "Użyj oddzielnego interfejsu, aby zdefiniować interfejs w jednym pakiecie, ale zaimplementuj go w innym. W ten sposób klient, który potrzebuje zależności do interfejsu może być całkowicie nieświadomy implementacji."

Po wzorzec interfejsu rozdzielanego umożliwia warstwy aplikacji (w tym przypadku projektu interfejsu API sieci Web dla mikrousług) mają zależność od wymagań zdefiniowanych w modelu domeny, ale nie bezpośrednią zależność od warstwy infrastruktury/trwałości. Ponadto można użyć iniekcji zależności do izolowania implementacji, która jest implementowana w warstwie infrastruktury/ trwałości przy użyciu repozytoriów.

Na przykład w poniższym przykładzie z interfejsem IOrderRepository definiuje, jakie operacje klasa OrderRepository będzie musiała zaimplementować w warstwie infrastruktury. W bieżącej implementacji aplikacji kod musi po prostu dodać lub zaktualizować zamówienia do bazy danych, ponieważ zapytania są dzielone zgodnie z uproszczonym podejściem CQRS.

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

- **Martin Fowler. Oddzielony interfejs.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Poprzedni](net-core-microservice-domain-model.md)
>[następny](implement-value-objects.md)
