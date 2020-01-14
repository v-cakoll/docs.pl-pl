---
title: Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Użyj koncepcji seedwork jako punktu wyjścia, aby rozpocząć implementację modelu domeny zorientowanego na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 491ff39f493a8f5ab192dc4a8376f560a8a7624b
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937176"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)

Folder rozwiązania zawiera folder *SeedWork* . Ten folder zawiera niestandardowe klasy bazowe, których można użyć jako podstawy dla jednostek domeny i obiektów wartości. Użyj tych klas bazowych, aby nie mieć nadmiarowego kodu w klasie obiektów każdej domeny. Folder dla tych typów klas ma nazwę *SeedWork* , a nie coś podobnego do *struktury*. Jest on nazywany *SeedWork* , ponieważ folder zawiera tylko niewielki podzbiór klas do wielokrotnego użytku, które nie mogą być uważane za strukturę. *Seedwork* jest terminem wprowadzonym przez [Michaely](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) i popularnym przez [Fowlera](https://martinfowler.com/bliki/Seedwork.html) , ale można również nazwać ten folder wspólny, SharedKernel lub podobny.

Rysunek 7-12 przedstawia klasy, które tworzą seedwork modelu domeny w mikrousłudze porządkowania. Zawiera kilka niestandardowych klas bazowych, takich jak Entity, Valueobject i Enumeration, oraz kilka interfejsów. Te interfejsy (IRepository i IUnitOfWork) informują warstwę infrastruktury o tym, co należy zaimplementować. Te interfejsy są również używane za pośrednictwem iniekcji zależności z warstwy aplikacji.

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Zrzut ekranu klas znajdujących się w folderze SeedWork":::
Szczegółowa zawartość folderu SeedWork zawierającego klasy podstawowe i interfejsy: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs i ValueObject.cs.
:::image-end:::

**Rysunek 7-12**. Przykładowy zestaw klas i interfejsów bazowych modelu domeny "seedwork"

Jest to typ kopiowania i wklejania wielokrotnego użytku, który wielu deweloperów udostępnia między projektami, a nie z nieoficjalną strukturą. Możesz mieć seedworks z dowolną warstwą lub biblioteką. Jeśli jednak zestaw klas i interfejsów jest wystarczająco duży, można utworzyć pojedynczą bibliotekę klas.

## <a name="the-custom-entity-base-class"></a>Klasa bazowa jednostki niestandardowej

Poniższy kod jest przykładem klasy podstawowej jednostki, w której można umieścić kod, który może być używany w taki sam sposób przez dowolną jednostkę domeny, taką jak identyfikator jednostki, [Operatory równości](../../../csharp/language-reference/operators/equality-operators.md), lista zdarzeń domeny na jednostkę itd.

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

Poprzedni kod korzystający z listy zdarzeń domeny na jednostkę zostanie przedstawiony w następnych sekcjach, gdy koncentruje się na zdarzeniach domeny.

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty repozytorium (interfejsy) w warstwie modelu domeny

Kontrakty repozytorium to po prostu interfejsy .NET, które wyrażają wymagania dotyczące kontraktu dla repozytoriów, które mają być używane dla każdej agregacji.

Repozytoria, z kodem EF Core lub innymi zależnościami infrastruktury i kodem (LINQ, SQL itp.), nie mogą być implementowane w ramach modelu domeny; repozytoria powinny implementować tylko interfejsy zdefiniowane w modelu domeny.

Wzorzec związany z tym postępowaniem (umieszczenie interfejsów repozytorium w warstwie modelu domeny) jest wzorcem interfejsu oddzielonego. Jak [wyjaśniono](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) w Fowlera, "Użyj rozdzielonego interfejsu do zdefiniowania interfejsu w jednym pakiecie, ale Zaimplementuj go w innym. W ten sposób klient wymagający zależności od interfejsu może być całkowicie nieświadomy implementacji. "

Po zastosowaniu wzorca interfejsu oddzielonego można korzystać z warstwy aplikacji (w tym przypadku projekt internetowego interfejsu API dla mikrousługi) ma zależność od wymagań zdefiniowanych w modelu domeny, ale nie jest bezpośrednim zależnością infrastruktury/warstwy trwałości. Ponadto można użyć iniekcji zależności, aby odizolować implementację, która jest zaimplementowana w warstwie infrastruktura/trwałość przy użyciu repozytoriów.

Na przykład poniższy przykład z interfejsem IOrderRepository definiuje, jakie operacje Klasa OrderRepository będzie musiała zostać wdrożona w warstwie infrastruktury. W bieżącej implementacji aplikacji kod po prostu musi dodać lub zaktualizować zamówienia do bazy danych, ponieważ zapytania są podzielone po uproszczone podejście CQRS.

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

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Fowlera Martin. Oddzielony interfejs.** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[Poprzedni](net-core-microservice-domain-model.md)
>[Następny](implement-value-objects.md)
