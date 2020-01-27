---
title: Nazwy klas, struktur i interfejsów
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727783"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nazwy klas, struktur i interfejsów
Poniższe wskazówki dotyczące nazewnictwa mają zastosowanie do ogólnego nazewnictwa typów.

 ✔️ DO nazw klas i struktur z rzeczownikami lub rzeczownikami, za pomocą PascalCasing.

 Spowoduje to odróżnienie nazw typów od metod, które są nazywane wyrażeniami czasownik.

 ✔️ DO interfejsów nazw przy użyciu fraz przymiotników lub od czasu do czas z rzeczownikami lub frazami rzeczowniknymi.

 Rzeczowniki i frazy rzeczowników powinny być używane rzadko i mogą wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsem.

 ❌ nie dają nazw klas prefiksem (np. "C").

 ✔️ Rozważ zakończenie nazwy klas pochodnych o nazwie klasy bazowej.

 Jest to bardzo czytelne i jasno wyjaśniono relację. Przykładami tego kodu jest: `ArgumentOutOfRangeException`, który jest rodzajem `Exception`i `SerializableAttribute`, który jest rodzajem `Attribute`. Jednak ważne jest, aby użyć odpowiednich orzeczeń w zastosowaniu niniejszych wytycznych; na przykład Klasa `Button` jest rodzajem zdarzenia `Control`, chociaż `Control` nie pojawia się w jego nazwie.

 ✔️ NALEŻY prefiksować nazwy interfejsów z literą I, aby wskazać, że typ jest interfejsem.

 Na przykład, `IComponent` (rzeczownik opisowy), `ICustomAttributeProvider` (phrase rzeczownik) i `IPersistable` (przymiotnik) są odpowiednimi nazwami interfejsów. Podobnie jak w przypadku innych nazw typów, należy unikać skrótów.

 ✔️ Upewnij się, że nazwy różnią się tylko prefiksem "I" w nazwie interfejsu podczas definiowania pary interfejsów klasy, w których Klasa jest implementacją standardową interfejsu.

## <a name="names-of-generic-type-parameters"></a>Nazwy parametrów typu ogólnego
 Typy ogólne zostały dodane do .NET Framework 2,0. Funkcja wprowadziła nowy rodzaj identyfikatora o nazwie *parametr typu*.

 ✔️ nazywają ogólne parametry typu z nazwami opisowymi, chyba że jednoliterowa nazwa nie jest całkowicie oczywista, a nazwa opisowa nie będzie dodawać wartości.

 ✔️ ROZWAŻYĆ użycie `T` jako nazwy parametru typu dla typów z jednym jednoliterowym parametrem typu.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ NALEŻY prefiksować nazwy parametrów typu opisowego z `T`.

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ ROZWAŻYĆ wskazanie ograniczeń umieszczanych na parametrze typu w nazwie parametru.

 Na przykład parametr ograniczony do `ISession` może być wywołany `TSession`.

## <a name="names-of-common-types"></a>Nazwy typów wspólnych
 ✔️ Postępuj zgodnie z wytycznymi opisanymi w poniższej tabeli podczas nazewnictwa typów pochodnych lub implementacji niektórych typów .NET Framework.

|Typ podstawowy|Wytyczne typu pochodnego/implementującego|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ dodać sufiks "Attribute" do nazw klas atrybutów niestandardowych.|
|`System.Delegate`|✔️ Dodaj sufiks "EventHandler" do nazw delegatów używanych w zdarzeniach.<br /><br /> ✔️ Dodaj sufiks "wywołanie zwrotne" do nazw delegatów innych niż te używane jako programy obsługi zdarzeń.<br /><br /> ❌ nie dodawaj sufiksu "delegat" do delegata.|
|`System.EventArgs`|✔️ dodać sufiks "EventArgs".|
|`System.Enum`|❌ nie pochodzą od tej klasy; Zamiast tego należy użyć słowa kluczowego obsługiwanego przez język; na przykład w C#, użyj słowa kluczowego `enum`.<br /><br /> ❌ nie dodawać sufiksu "enum" ani "flag".|
|`System.Exception`|✔️ Dodaj sufiks "Exception".|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ dodać sufiks "dictionary". Należy zauważyć, że `IDictionary` jest określonym typem kolekcji, ale wskazówki te mają pierwszeństwo przed bardziej ogólnymi wskazówkami dotyczącymi kolekcji.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ dodać sufiks "Kolekcja".|
|`System.IO.Stream`|✔️ dodać sufiks "Stream".|
|`CodeAccessPermission IPermission`|✔️ dodać sufiks "uprawnienie".|

## <a name="naming-enumerations"></a>Wyliczanie nazw
 Nazwy typów wyliczeniowych (nazywane również wyliczeniami) ogólnie powinny być zgodne ze standardowymi regułami nazewnictwa typów (PascalCasing itp.). Istnieją jednak dodatkowe wytyczne, które dotyczą wyłącznie wyliczeń.

 ✔️ do wyliczenia należy używać pojedynczej nazwy typu, chyba że jej wartości są polami bitowymi.

 ✔️ należy używać nazwy typu w liczbie mnogiej dla wyliczenia z polami bitowymi jako wartości, nazywane również flagami enum.

 ❌ nie używać sufiksu "enum" w nazwach typów wyliczeniowych.

 ❌ nie używaj sufiksów "flag" lub "flags" w nazwach typów wyliczeniowych.

 ❌ nie używać prefiksu dla nazw wartości wyliczenia (np. "AD" dla wyliczeń ADO, "RTF" dla tekstu sformatowanego RTF itp.).

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
