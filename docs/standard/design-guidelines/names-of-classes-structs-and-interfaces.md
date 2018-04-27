---
title: Nazwy klasy, struktury i interfejsy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bcb3d1c636c8f846be8290738f322f36e09c9dad
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="names-of-classes-structs-and-interfaces"></a>Nazwy klasy, struktury i interfejsy
Nazewnictwa wskazówki, które należy wykonać dotyczą nazw typu ogólnego.  
  
 **CZY ✓** nazwy klas i struktur rzeczowniki lub fraz rzeczownik, przy użyciu PascalCasing.  
  
 Nazwy typów to odróżnia od metody, które są nazywane zlecenie fraz.  
  
 **CZY ✓** nazwy interfejsów przymiotników fraz lub czasami rzeczowniki ani fraz rzeczownik.  
  
 Rzeczowniki i fraz rzeczownik powinny być rzadko używane i może wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsu.  
  
 **X nie** nadaj nazwę klasy prefiksu (np. "C").  
  
 **ROZWAŻ ✓** kończy nazwę klasy o nazwie klasy podstawowej pochodne.  
  
 To jest bardzo czytelny i wyraźnie wyjaśniono relacji. Przykłady to w kodzie: `ArgumentOutOfRangeException`, który jest rodzajem z `Exception`, i `SerializableAttribute`, który jest rodzajem z `Attribute`. Jednak ważne jest, aby użyć uzasadnione ocenie w zastosowanie niniejsze wytyczne; na przykład `Button` klasy jest rodzajem elementu `Control` zdarzeń, mimo że `Control` nie pojawia się w jego nazwę.  
  
 **CZY ✓** interfejsu prefiksu nazwy z literą I, aby wskazać, że typ jest interfejsem.  
  
 Na przykład `IComponent` (rzeczownik opisową), `ICustomAttributeProvider` (rzeczownik oznaczenie), i `IPersistable` (przymiotnik) są nazwy odpowiedniego interfejsu. Podobnie jak w przypadku innych nazw typów Unikaj skrótów.  
  
 **CZY ✓** upewnij się, że nazwy są różne tylko przez "I" prefiksu nazwy interfejsu podczas definiowania parę klasy — interfejs klasy w przypadku standardowej implementacji interfejsu.  
  
## <a name="names-of-generic-type-parameters"></a>Nazwy parametrów typu ogólnego  
 Typy ogólne zostały dodane do programu .NET Framework 2.0. Funkcja wprowadzono nowy rodzaj identyfikatora zwanego *parametr typu*.  
  
 **CZY ✓** nazwa parametry typu ogólnego z nazw opisowych, chyba że jednym litera jest całkowicie oczywiste i nazwę opisową nie może dodać wartość.  
  
 **ROZWAŻ ✓** przy użyciu `T` jako nazwę parametru typu dla typów z jednym parametrem litery jednego typu.  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **CZY ✓** prefiksu nazwy parametrów typu opisową z `T`.  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **ROZWAŻ ✓** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.  
  
 Na przykład parametr ograniczone do `ISession` może zostać wywołana `TSession`.  
  
## <a name="names-of-common-types"></a>Nazwy typów wspólnych  
 **CZY ✓** postępuj zgodnie z wytycznymi opisane w poniższej tabeli w nazwach typów pochodnych lub wykonania pewnych typów .NET Framework.  
  
|Typ podstawowy|Wytyczna typu pochodnego implementacja|  
|---------------|------------------------------------------|  
|`System.Attribute`|**CZY ✓** dodać sufiks "Atrybutu" do nazwy klasy atrybutu niestandardowego.|  
|`System.Delegate`|**CZY ✓** dodać sufiks "EventHandler" do nazwy obiektów delegowanych, które są używane w zdarzeniach.<br /><br /> **CZY ✓** dodać sufiks "Wywołania zwrotnego" do nazwy obiektów delegowanych innych niż te używane jako procedury obsługi zdarzeń.<br /><br /> **X nie** dodać sufiks "Delegowanie" do delegata.|  
|`System.EventArgs`|**CZY ✓** dodać sufiks "EventArgs."|  
|`System.Enum`|**X nie** pochodzi od tej klasy; użyj słowa kluczowego zamiast obsługiwane przez język; na przykład w języku C#, użyj `enum` — słowo kluczowe.<br /><br /> **X nie** dodać sufiks "Enum" lub "Flaga".|  
|`System.Exception`|**CZY ✓** dodać sufiks "Wyjątku."|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**CZY ✓** dodać sufiks "Słownik". Należy pamiętać, że `IDictionary` jest określonego typu kolekcji, ale ta wytyczna ma pierwszeństwo przed bardziej ogólne wytyczne kolekcje, poniżej.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**CZY ✓** dodać sufiksem "Collection".|  
|`System.IO.Stream`|**CZY ✓** dodać sufiks "Strumień".|  
|`CodeAccessPermission IPermission`|**CZY ✓** dodać sufiks "Uprawnienia."|  
  
## <a name="naming-enumerations"></a>Wyliczenia nazw  
 Ogólnie rzecz biorąc nazwy Typy wyliczeniowe (nazywanych również wyliczenia) należy wykonać standardowe reguły nazewnictwa typu (PascalCasing itp.). Istnieją dodatkowe wskazówki, które dotyczą przede wszystkim wyliczenia.  
  
 **CZY ✓** Użyj nazwy typu pojedynczej wyliczania, chyba że jego wartości pól bitowych.  
  
 **CZY ✓** Użyj nazwy typu w liczbie mnogiej wyliczania z pól bitowych jako wartości, nazywane również wyliczenia flag.  
  
 **X nie** Użyj sufiksu "Enum" w nazwach typów wyliczenia.  
  
 **X nie** Użyj "Flaga" lub nazwy typów, sufiksy "Flag" w elemencie enum.  
  
 **X nie** Użyj prefiksu nazwy wartości wyliczenia (np. "ad" do wyliczenia obiektów ADO.), "format rtf" dla wyliczenia RTF itd.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
