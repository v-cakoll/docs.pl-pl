---
title: Nazwy klas, struktur i interfejsów
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c56f840bc5ebd5070c9b686384751acab3f0203
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44706076"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nazwy klas, struktur i interfejsów
Wskazówkami nazewnictwa, które należy wykonać dotyczą nazewnictwa typ ogólny.  
  
 **✓ DO** nazwy klas i struktur rzeczowniki lub fraz rzeczownik, przy użyciu PascalCasing.  
  
 Nazwy typów to odróżnia od metody, które są nazywane oraz oznaczenia zlecenie.  
  
 **✓ DO** nazwy interfejsów przymiotników fraz lub czasami rzeczowniki ani fraz rzeczownik.  
  
 Rzeczowniki i fraz rzeczownik powinny być rzadko używane i może wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsu.  
  
 **X DO NOT** nadaj nazwę klasy prefiksu (np. "C").  
  
 **✓ CONSIDER** kończy nazwę klasy o nazwie klasy podstawowej pochodne.  
  
 To jest bardzo czytelny i wyraźnie opisano relację. Oto kilka przykładów tego kodu: `ArgumentOutOfRangeException`, który jest rodzajem z `Exception`, i `SerializableAttribute`, co jest rodzajem z `Attribute`. Jednak warto użyć uzasadnione orzeczenia stosowania ta wytyczna; na przykład `Button` klasy jest rodzajem elementu `Control` zdarzeń, mimo że `Control` nie pojawia się w jego nazwę.  
  
 **✓ DO** interfejsu prefiksu nazwy z literą I, aby wskazać, że typ jest interfejsem.  
  
 Na przykład `IComponent` (opisowego rzeczownika) `ICustomAttributeProvider` (rzeczownik oznaczenie), i `IPersistable` (przymiotnik) są nazwami odpowiedniego interfejsu. Podobnie jak w przypadku innych nazwami typów, unikaj skrótów.  
  
 **✓ DO** upewnij się, że nazwy są różne tylko przez "I" prefiksu nazwy interfejsu podczas definiowania parę klasy — interfejs klasy w przypadku standardowej implementacji interfejsu.  
  
## <a name="names-of-generic-type-parameters"></a>Nazwy parametrów typu ogólnego  
 Typy ogólne zostały dodane do programu .NET Framework 2.0. Wprowadzonej nowego rodzaju identyfikatora zwanego *parametr typu*.  
  
 **✓ DO** nazwa parametry typu ogólnego z nazw opisowych, chyba że jednym litera jest całkowicie oczywiste i nazwę opisową nie może dodać wartość.  
  
 **✓ CONSIDER** przy użyciu `T` jako nazwę parametru typu dla typów z jednym parametrem litery jednego typu.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** prefiksu nazwy parametrów typu opisową z `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.  
  
 Na przykład parametr ograniczone do `ISession` może być wywoływana `TSession`.  
  
## <a name="names-of-common-types"></a>Nazwy typów wspólnych  
 **✓ DO** postępuj zgodnie z wytycznymi opisane w poniższej tabeli w nazwach typów pochodnych lub wykonania pewnych typów .NET Framework.  
  
|Typ podstawowy|Pochodne Implementowanie wskazówek dotyczących typów|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** dodać sufiks "Atrybutu" do nazwy klasy atrybutu niestandardowego.|  
|`System.Delegate`|**✓ DO** dodać sufiks "EventHandler" do nazwy obiektów delegowanych, które są używane w zdarzeniach.<br /><br /> **✓ DO** dodać sufiks "Wywołania zwrotnego" do nazwy obiektów delegowanych innych niż te używane jako procedury obsługi zdarzeń.<br /><br /> **X DO NOT** dodać sufiks "Delegowanie" do delegata.|  
|`System.EventArgs`|**✓ DO** dodać sufiks "EventArgs."|  
|`System.Enum`|**X DO NOT** pochodzi od tej klasy; użyj słowa kluczowego zamiast obsługiwane przez język; na przykład w języku C#, użyj `enum` — słowo kluczowe.<br /><br /> **X DO NOT** dodać sufiks "Enum" lub "Flaga".|  
|`System.Exception`|**✓ DO** dodać sufiks "Wyjątku."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** dodać sufiks "Słownik". Należy pamiętać, że `IDictionary` jest określonego typu kolekcji, ale ta wytyczna ma pierwszeństwo przed bardziej ogólne wytyczne kolekcji, który następuje po.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** dodać sufiksem "Collection".|  
|`System.IO.Stream`|**✓ DO** dodać sufiks "Strumień".|  
|`CodeAccessPermission IPermission`|**✓ DO** dodać sufiks "Uprawnienia."|  
  
## <a name="naming-enumerations"></a>Nazwy wyliczeń  
 Ogólnie rzecz biorąc nazwy Typy wyliczeniowe (nazywane również Typy wyliczeniowe) powinien być zgodny standardowe reguły nazewnictwa typu (PascalCasing itp.). Jednakże istnieją dodatkowe wskazówki, które mają zastosowanie szczególnie w przypadku typów wyliczeniowych.  
  
 **✓ DO** Użyj nazwy typu pojedynczej wyliczania, chyba że jego wartości pól bitowych.  
  
 **✓ DO** Użyj nazwy typu w liczbie mnogiej wyliczania z pól bitowych jako wartości, nazywane również wyliczenia flag.  
  
 **X DO NOT** Użyj sufiksu "Enum" w nazwach typów wyliczenia.  
  
 **X DO NOT** Użyj "Flaga" lub nazwy typów, sufiksy "Flag" w elemencie enum.  
  
 **X DO NOT** Użyj prefiksu nazwy wartości wyliczenia (np. "ad" do wyliczenia obiektów ADO.), "format rtf" dla wyliczenia RTF itd.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
