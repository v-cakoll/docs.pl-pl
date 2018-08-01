---
title: Nazwy klasy, struktury i interfejsy
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
ms.openlocfilehash: a1841fbfcb76d5b56681b63ec4b39e9a7418707f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576145"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nazwy klasy, struktury i interfejsy
Nazewnictwa wskazówki, które należy wykonać dotyczą nazw typu ogólnego.  
  
 **✓ DO** nazwy klas i struktur rzeczowniki lub fraz rzeczownik, przy użyciu PascalCasing.  
  
 Nazwy typów to odróżnia od metody, które są nazywane zlecenie fraz.  
  
 **✓ DO** nazwy interfejsów przymiotników fraz lub czasami rzeczowniki ani fraz rzeczownik.  
  
 Rzeczowniki i fraz rzeczownik powinny być rzadko używane i może wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsu.  
  
 **X DO NOT** nadaj nazwę klasy prefiksu (np. "C").  
  
 **✓ CONSIDER** kończy nazwę klasy o nazwie klasy podstawowej pochodne.  
  
 To jest bardzo czytelny i wyraźnie wyjaśniono relacji. Przykłady to w kodzie: `ArgumentOutOfRangeException`, który jest rodzajem z `Exception`, i `SerializableAttribute`, który jest rodzajem z `Attribute`. Jednak ważne jest, aby użyć uzasadnione ocenie w zastosowanie niniejsze wytyczne; na przykład `Button` klasy jest rodzajem elementu `Control` zdarzeń, mimo że `Control` nie pojawia się w jego nazwę.  
  
 **✓ DO** interfejsu prefiksu nazwy z literą I, aby wskazać, że typ jest interfejsem.  
  
 Na przykład `IComponent` (rzeczownik opisową), `ICustomAttributeProvider` (rzeczownik oznaczenie), i `IPersistable` (przymiotnik) są nazwy odpowiedniego interfejsu. Podobnie jak w przypadku innych nazw typów Unikaj skrótów.  
  
 **✓ DO** upewnij się, że nazwy są różne tylko przez "I" prefiksu nazwy interfejsu podczas definiowania parę klasy — interfejs klasy w przypadku standardowej implementacji interfejsu.  
  
## <a name="names-of-generic-type-parameters"></a>Nazwy parametrów typu ogólnego  
 Typy ogólne zostały dodane do programu .NET Framework 2.0. Funkcja wprowadzono nowy rodzaj identyfikatora zwanego *parametr typu*.  
  
 **✓ DO** nazwa parametry typu ogólnego z nazw opisowych, chyba że jednym litera jest całkowicie oczywiste i nazwę opisową nie może dodać wartość.  
  
 **✓ CONSIDER** przy użyciu `T` jako nazwę parametru typu dla typów z jednym parametrem litery jednego typu.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** prefiksu nazwy parametrów typu opisową z `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.  
  
 Na przykład parametr ograniczone do `ISession` może zostać wywołana `TSession`.  
  
## <a name="names-of-common-types"></a>Nazwy typów wspólnych  
 **✓ DO** postępuj zgodnie z wytycznymi opisane w poniższej tabeli w nazwach typów pochodnych lub wykonania pewnych typów .NET Framework.  
  
|Typ podstawowy|Wytyczna typu pochodnego implementacja|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** dodać sufiks "Atrybutu" do nazwy klasy atrybutu niestandardowego.|  
|`System.Delegate`|**✓ DO** dodać sufiks "EventHandler" do nazwy obiektów delegowanych, które są używane w zdarzeniach.<br /><br /> **✓ DO** dodać sufiks "Wywołania zwrotnego" do nazwy obiektów delegowanych innych niż te używane jako procedury obsługi zdarzeń.<br /><br /> **X DO NOT** dodać sufiks "Delegowanie" do delegata.|  
|`System.EventArgs`|**✓ DO** dodać sufiks "EventArgs."|  
|`System.Enum`|**X DO NOT** pochodzi od tej klasy; użyj słowa kluczowego zamiast obsługiwane przez język; na przykład w języku C#, użyj `enum` — słowo kluczowe.<br /><br /> **X DO NOT** dodać sufiks "Enum" lub "Flaga".|  
|`System.Exception`|**✓ DO** dodać sufiks "Wyjątku."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** dodać sufiks "Słownik". Należy pamiętać, że `IDictionary` jest określonego typu kolekcji, ale ta wytyczna ma pierwszeństwo przed bardziej ogólne wytyczne kolekcje, poniżej.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** dodać sufiksem "Collection".|  
|`System.IO.Stream`|**✓ DO** dodać sufiks "Strumień".|  
|`CodeAccessPermission IPermission`|**✓ DO** dodać sufiks "Uprawnienia."|  
  
## <a name="naming-enumerations"></a>Wyliczenia nazw  
 Ogólnie rzecz biorąc nazwy Typy wyliczeniowe (nazywanych również wyliczenia) należy wykonać standardowe reguły nazewnictwa typu (PascalCasing itp.). Istnieją dodatkowe wskazówki, które dotyczą przede wszystkim wyliczenia.  
  
 **✓ DO** Użyj nazwy typu pojedynczej wyliczania, chyba że jego wartości pól bitowych.  
  
 **✓ DO** Użyj nazwy typu w liczbie mnogiej wyliczania z pól bitowych jako wartości, nazywane również wyliczenia flag.  
  
 **X DO NOT** Użyj sufiksu "Enum" w nazwach typów wyliczenia.  
  
 **X DO NOT** Użyj "Flaga" lub nazwy typów, sufiksy "Flag" w elemencie enum.  
  
 **X DO NOT** Użyj prefiksu nazwy wartości wyliczenia (np. "ad" do wyliczenia obiektów ADO.), "format rtf" dla wyliczenia RTF itd.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
