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
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353700"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nazwy klas, struktur i interfejsów
Poniższe wskazówki dotyczące nazewnictwa mają zastosowanie do ogólnego nazewnictwa typów.  
  
 **✓ DO** nazwy klas i struktur rzeczowniki lub fraz rzeczownik, przy użyciu PascalCasing.  
  
 Spowoduje to odróżnienie nazw typów od metod, które są nazywane wyrażeniami czasownik.  
  
 **✓ DO** nazwy interfejsów przymiotników fraz lub czasami rzeczowniki ani fraz rzeczownik.  
  
 Rzeczowniki i frazy rzeczowników powinny być używane rzadko i mogą wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsem.  
  
 **X DO NOT** nadaj nazwę klasy prefiksu (np. "C").  
  
 **✓ CONSIDER** kończy nazwę klasy o nazwie klasy podstawowej pochodne.  
  
 Jest to bardzo czytelne i jasno wyjaśniono relację. Oto kilka przykładów tego kodu: `ArgumentOutOfRangeException`, który jest rodzajem `Exception` i `SerializableAttribute`, który jest rodzajem `Attribute`. Jednak ważne jest, aby użyć odpowiednich orzeczeń w zastosowaniu niniejszych wytycznych; na przykład Klasa `Button` jest rodzajem zdarzenia `Control`, chociaż `Control` nie pojawia się w jego nazwie.  
  
 **✓ DO** interfejsu prefiksu nazwy z literą I, aby wskazać, że typ jest interfejsem.  
  
 Na przykład, `IComponent` (opis rzeczownik), `ICustomAttributeProvider` (phrase rzeczownik) i `IPersistable` (przymiotnik) są odpowiednimi nazwami interfejsów. Podobnie jak w przypadku innych nazw typów, należy unikać skrótów.  
  
 **✓ DO** upewnij się, że nazwy są różne tylko przez "I" prefiksu nazwy interfejsu podczas definiowania parę klasy — interfejs klasy w przypadku standardowej implementacji interfejsu.  
  
## <a name="names-of-generic-type-parameters"></a>Nazwy parametrów typu ogólnego  
 Typy ogólne zostały dodane do .NET Framework 2,0. Funkcja wprowadziła nowy rodzaj identyfikatora o nazwie *parametr typu*.  
  
 **✓ DO** nazwa parametry typu ogólnego z nazw opisowych, chyba że jednym litera jest całkowicie oczywiste i nazwę opisową nie może dodać wartość.  
  
 **✓ CONSIDER** przy użyciu `T` jako nazwę parametru typu dla typów z jednym parametrem litery jednego typu.  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** prefiksu nazwy parametrów typu opisową z `T`.  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.  
  
 Na przykład parametr ograniczony do `ISession` może być wywołany `TSession`.  
  
## <a name="names-of-common-types"></a>Nazwy typów wspólnych  
 **✓ DO** postępuj zgodnie z wytycznymi opisane w poniższej tabeli w nazwach typów pochodnych lub wykonania pewnych typów .NET Framework.  
  
|Typ podstawowy|Wytyczne typu pochodnego/implementującego|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** dodać sufiks "Atrybutu" do nazwy klasy atrybutu niestandardowego.|  
|`System.Delegate`|**✓ DO** dodać sufiks "EventHandler" do nazwy obiektów delegowanych, które są używane w zdarzeniach.<br /><br /> **✓ DO** dodać sufiks "Wywołania zwrotnego" do nazwy obiektów delegowanych innych niż te używane jako procedury obsługi zdarzeń.<br /><br /> **X DO NOT** dodać sufiks "Delegowanie" do delegata.|  
|`System.EventArgs`|**✓ DO** dodać sufiks "EventArgs."|  
|`System.Enum`|**X DO NOT** pochodzi od tej klasy; użyj słowa kluczowego zamiast obsługiwane przez język; na przykład w języku C#, użyj `enum` — słowo kluczowe.<br /><br /> **X DO NOT** dodać sufiks "Enum" lub "Flaga".|  
|`System.Exception`|**✓ DO** dodać sufiks "Wyjątku."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** dodać sufiks "Słownik". Należy pamiętać, że `IDictionary` jest określonym typem kolekcji, ale wskazówki te mają pierwszeństwo przed bardziej ogólnymi wskazówkami dotyczącymi kolekcji.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** dodać sufiksem "Collection".|  
|`System.IO.Stream`|**✓ DO** dodać sufiks "Strumień".|  
|`CodeAccessPermission IPermission`|**✓ DO** dodać sufiks "Uprawnienia."|  
  
## <a name="naming-enumerations"></a>Wyliczanie nazw  
 Nazwy typów wyliczeniowych (nazywane również wyliczeniami) ogólnie powinny być zgodne ze standardowymi regułami nazewnictwa typów (PascalCasing itp.). Istnieją jednak dodatkowe wytyczne, które dotyczą wyłącznie wyliczeń.  
  
 **✓ DO** Użyj nazwy typu pojedynczej wyliczania, chyba że jego wartości pól bitowych.  
  
 **✓ DO** Użyj nazwy typu w liczbie mnogiej wyliczania z pól bitowych jako wartości, nazywane również wyliczenia flag.  
  
 **X DO NOT** Użyj sufiksu "Enum" w nazwach typów wyliczenia.  
  
 **X DO NOT** Użyj "Flaga" lub nazwy typów, sufiksy "Flag" w elemencie enum.  
  
 **X DO NOT** Użyj prefiksu nazwy wartości wyliczenia (np. "ad" do wyliczenia obiektów ADO.), "format rtf" dla wyliczenia RTF itd.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Reprinted przez uprawnienie Pearson Education, Inc. od [Framework — wytyczne dotyczące projektowania: Konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, druga wersja @ no__t-0 przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
