---
title: Seedwork (może być ponownie używane klasy podstawowe i interfejsy dla modelu domeny)
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Seedwork (może być ponownie używane klasy podstawowe i interfejsy dla modelu domeny)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 7098bc1d37ecdf4826c0db6e754ca8df2ed72fe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578056"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (może być ponownie używane klasy podstawowe i interfejsy dla modelu domeny)

Folder rozwiązania zawiera *SeedWork* folderu. *SeedWork* folder zawiera niestandardowej klasy bazowej, która służy jako podstawa dla domeny jednostek i obiektów wartość. Należy używać tych klas podstawowych, dlatego nie masz nadmiarowy kod w klasie obiektów w każdej domenie. Folder dla tego typu klasy jest nazywany *SeedWork* i nie coś, takich jak *Framework*. Jest to *SeedWork* ponieważ folder zawiera tylko mały podzbiór klasy wielokrotnego użytku, które naprawdę nie może być uważane za struktury. *Seedwork* termin wprowadzone przez [piór Michael](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) i popularized przez [Fowler pole](https://martinfowler.com/bliki/Seedwork.html) , ale można również nazwę tego folderu wspólne, SharedKernel, lub podobny.

Rysunek 9 – 12 zawiera klasy, które tworzą seedwork modelu domeny w mikrousługi porządkowania. Ma kilka niestandardowych klas podstawowych takich jak jednostki, ValueObject i wyliczenia, a także kilka interfejsów. Te interfejsy (IRepository i IUnitOfWork) informuje warstwie infrastrukturze o co musi zostać wdrożone. Te interfejsy są również używane przez iniekcji zależności od warstwy aplikacji.

![](./media/image13.PNG)

**Rysunek 9 – 12**. Przykładowy zestaw klasy podstawowej "seedwork" model domeny i interfejsy

Jest to typ, kopiowania i wklejania ponownego użycia wielu deweloperów udziale między projektami, formalnych ram. Może mieć seedworks w dowolnej warstwy lub biblioteki. Jednak zestaw klasy i interfejsy pobiera wystarczająco duży, możesz utworzyć bibliotekę jednej klasy.

## <a name="the-custom-entity-base-class"></a>Niestandardowe klasy podstawowej jednostki

Następujący kod jest przykładem klasy podstawowej jednostki lokalizację kodu, który może służyć samo przez osobę domeny, takich jak identyfikator jednostki [Operatory równości](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), listy zdarzeń domeny na jednostki itp.

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
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

Poprzedni kod przy użyciu listy zdarzeń domeny na jednostkę opisano w kolejnych sekcjach podczas koncentrujących się na zdarzenia domeny. 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Kontrakty repozytorium (interfejsy) w warstwie modelu domeny

Kontrakty repozytorium są po prostu interfejsów .NET, które express wymagania umowy repozytoriów do zastosowania w przypadku każdego agregacji. 

Repozytoria się z kodem EF podstawowe lub inne zależności infrastruktury i kodu (Linq, SQL, itp.), nie może być realizowana w ramach modelu domeny; repozytoria tylko powinien implementować interfejsów, które należy zdefiniować. 

Wzorzec związane z tym rozwiązaniem (wprowadzenie do interfejsów repozytorium warstwy modelu domeny) jest wzorzec oddzielone interfejsu. Jako [wyjaśniono](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) przez Fowler pole "Użyj interfejsu oddzielone można zdefiniować interfejs w jednej pakietu, ale ją wdrożyć w innym. W ten sposób klient, który wymaga zależności do interfejsu może być dostarczanie implementacji."

Po wzorzec oddzielone interfejs umożliwia ma zależności od wymagań zdefiniowanych w modelu domeny, ale nie bezpośrednie zależności do infrastruktury/trwałości warstwy aplikacji (w tym przypadku projekt interfejsu API sieci Web do mikrousługi) warstwy. Ponadto iniekcji zależności można użyć do izolowania implementację, która jest zaimplementowana w infrastrukturze / warstwę trwałości przy użyciu repozytoriów.

Na przykład w poniższym przykładzie z interfejsem IOrderRepository zdefiniowano jakie operacje OrderRepository klasy należy zaimplementować w warstwie infrastrukturze. Bieżąca implementacja aplikacji kod właśnie musi dodać lub zaktualizować zamówień w bazie danych, ponieważ zapytania są podzielone na następujące podejście CQRS uproszczone.

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

-   **Pole Fowler. Interfejs rozdzielone.**
    [*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)


>[!div class="step-by-step"]
[Poprzednie] (net-core mikrousługi domeny model.md) [dalej] (wdrożenie — wartość objects.md)
