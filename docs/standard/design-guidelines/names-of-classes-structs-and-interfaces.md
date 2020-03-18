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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400597"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nazwy klas, struktur i interfejsów
Poniższe wskazówki dotyczące nazewnictwa dotyczą nazewnictwa typu ogólnego.

 ✔️ do klas nazw i struktur z rzeczownikami lub frazami rzeczownikowymi, za pomocą PascalCasing.

 Rozróżnia nazwy typów od metod, które są nazywane frazami czasownikowymi.

 ✔️ do interfejsów nazw z przymiotnikami lub od czasu do czasu z rzeczownikami lub frazami rzeczowników.

 Rzeczowniki i rzeczowniki powinny być używane rzadko i mogą wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsem.

 ❌NIE należy podawać nazw klas prefiks (np.

 ✔️ ZASTANÓW SIĘ, kończąc nazwę klas pochodnych nazwą klasy podstawowej.

 Jest to bardzo czytelne i wyraźnie wyjaśnia związek. Niektóre przykłady tego w kodzie `ArgumentOutOfRangeException`to: , `Exception`który `SerializableAttribute`jest rodzajem `Attribute`, i , który jest rodzajem . Jednakże ważne jest, aby stosować rozsądną ocenę przy stosowaniu niniejszych wytycznych; na przykład `Button` klasa jest rodzajem `Control` zdarzenia, chociaż `Control` nie pojawia się w jego nazwie.

 ✔️ nazwy interfejsu prefiksu DO z literą I, aby wskazać, że typ jest interfejsem.

 Na przykład `IComponent` (rzeczownik opisowy), `ICustomAttributeProvider` (fraza rzeczownikowa) i `IPersistable` (przymiotnik) są odpowiednimi nazwami interfejsu. Podobnie jak w przypadku innych nazw typów, należy unikać skrótów.

 ✔️ upewnij się, że nazwy różnią się tylko przez prefiks "I" na nazwę interfejsu podczas definiowania pary klasy interfejsu, gdzie klasa jest standardową implementacją interfejsu.

## <a name="names-of-generic-type-parameters"></a>Nazwy parametrów typu ogólnego
 Generycznych zostały dodane do .NET Framework 2.0. Funkcja wprowadziła nowy rodzaj identyfikatora o nazwie *parametr typu*.

 ✔️ DO nazwa ogólnych parametrów typu z opisowymi nazwami, chyba że nazwa jednoliterowa jest całkowicie oczywista i nazwa opisowa nie doda wartości.

 ✔️ ZASTANÓW SIĘ, używając `T` jako nazwy parametru typu dla typów z jednym parametrem typu jednoliterowego.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DO prefiksu nazwy parametrów `T`typu opisowego z .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ ROZWAŻ Wskazanie ograniczeń umieszczonych na parametrze typu w nazwie parametru.

 Na przykład parametr ograniczony do `ISession` może `TSession`być wywoływana .

## <a name="names-of-common-types"></a>Nazwy typów wspólnych
 ✔️ wykonaj wytyczne opisane w poniższej tabeli podczas nazywania typów pochodzących z lub implementowania niektórych typów .NET Framework.

|Typ podstawowy|Wytyczne dotyczące typu pochodnego/wykonawczego|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ DO dodać sufiks "Atrybut" do nazw klas atrybutów niestandardowych.|
|`System.Delegate`|✔️ DO dodać sufiks "EventHandler" do nazw delegatów, które są używane w zdarzeniach.<br /><br /> ✔️ DO dodać sufiks "Wywołanie zwrotu" do nazw delegatów innych niż te używane jako programy obsługi zdarzeń.<br /><br /> ❌NIE dodawaj sufiksu "Delegować" do pełnomocnika.|
|`System.EventArgs`|✔️ DO dodać sufiks "EventArgs".|
|`System.Enum`|❌NIE wywodzić z tej klasy; zamiast tego użyj słowa kluczowego obsługiwanego przez twój język; na przykład w języku `enum` C#, użyj słowa kluczowego.<br /><br /> ❌NIE dodawaj sufiksu "Wyliczenie" ani "Flaga".|
|`System.Exception`|✔️ DO dodać sufiks "Wyjątek".|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ DO dodać sufiks "Słownik". Należy `IDictionary` zauważyć, że jest to określony typ kolekcji, ale ta wskazówka ma pierwszeństwo przed bardziej ogólne wskazówki kolekcje, które następuje.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ DO dodać sufiks "Kolekcja".|
|`System.IO.Stream`|✔️ DO dodać przyrostek "Strumień".|
|`CodeAccessPermission IPermission`|✔️ DO dodać sufiks "Uprawnienie".|

## <a name="naming-enumerations"></a>Nazewnictwo Wyliczenia
 Nazwy typów wyliczenia (nazywane również wyliczeniami) w ogóle powinny być zgodne ze standardowymi regułami nazewnictwa typu (PascalCasing itp.). Istnieją jednak dodatkowe wytyczne, które mają zastosowanie specjalnie do wyliczenia.

 ✔️ do używania nazwy typu pojedynczego dla wyliczenia, chyba że jego wartości są pola bitowe.

 ✔️ DO używać nazwy typu liczby mnogiej dla wyliczenia z pól bitowych jako wartości, nazywane również flagi wyliczenia.

 ❌NIE należy używać sufiksu "Wyliczenie" w nazwach typów wyliczenia.

 ❌NIE należy używać sufiksów "Flag" ani "Flags" w nazwach typów wyliczenia.

 ❌NIE należy używać prefiksu w nazwach wartości wyliczenia (np. "ad" dla wyliczeń ADO, "rtf" dla wyliczeń tekstu sformatnego itp.).

 *Części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms i Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowane 22 października 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development Series.*

## <a name="see-also"></a>Zobacz też

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
