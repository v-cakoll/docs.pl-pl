---
title: "Konwencje wielkość liter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b36f230c9a5f8653f3e252d26fe6464bb9cac4bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="capitalization-conventions"></a>Konwencje wielkość liter
Wskazówki zawarte w ten rozdział układ prostą metodę przy użyciu przypadek, który po zastosowaniu spójnie upewnij identyfikatory typów, członków i parametry łatwy do odczytania.  
  
## <a name="capitalization-rules-for-identifiers"></a>Reguły wielkości liter dla identyfikatorów  
 Rozróżnianie słów w identyfikatorze, wielką pierwszą literę każdego wyrazu w identyfikatorze. Nie używaj znaków podkreślenia rozróżnianie słów, lub dla tej sprawy w dowolnym miejscu identyfikatorów. Istnieją dwa sposoby odpowiednie na wielką identyfikatorów, w zależności od użycia identyfikatora:  
  
-   PascalCasing  
  
-   camelCasing  
  
 Konwencji PascalCasing używany dla wszystkich identyfikatorów z wyjątkiem nazwy parametrów powoduje rozpoczynanie pierwszy znak każdego wyrazu (w tym akronimów za pośrednictwem dwóch liter o długości), jak pokazano w poniższych przykładach:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Szczególnych przypadkach wykonywane akronimów dwuliterowych, w których kapitalizacji zarówno litery, jak pokazano w następującym identyfikatorem:  
  
 `IOStream`  
  
 Konwencja camelCasing, używana tylko w przypadku nazw parametrów powoduje rozpoczynanie pierwszy znak każdego wyrazu, z wyjątkiem pierwszej word, jak pokazano w poniższych przykładach. Jako przykład przedstawiono również, akronimów dwuliterowych, rozpoczynające się identyfikatorem liter formatu są małymi literami.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **CZY ✓** Użyj PascalCasing dla wszystkich publicznych nazw elementu członkowskiego, typ i przestrzeń nazw składającą się z wielu wyrazów.  
  
 **CZY ✓** camelCasing na użytek nazwy parametrów.  
  
 W poniższej tabeli opisano reguły wielkości liter dla różnych typów identyfikatorów.  
  
|Identyfikator|Wielkość znaków|Przykład|  
|----------------|------------|-------------|  
|Przestrzeń nazw|Pascal|`namespace System.Security { ... }`|  
|Typ|Pascal|`public class StreamReader { ... }`|  
|Interface|Pascal|`public interface IEnumerable { ... }`|  
|Metoda|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Właściwość|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Zdarzenie|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Pole|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Wartość wyliczenia|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametr|Formatu|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Zamiany wyrazy złożone i typowe terminy  
 Większość warunki złożone są traktowane jako pojedyncze wyrazy na potrzeby użycia wielkich liter.  
  
 **X nie** własne w tzw wyrazy złożone zamknąć formularz.  
  
 Są zapisywane jako pojedynczego wyrazu, takie jak punkt końcowy wyrazy złożone. Na potrzeby wielkości liter dla skrótowców Traktuj wyraz złożony zamknięciu formularza jako pojedynczego wyrazu. Użyj bieżącego słownika, aby określić, czy wyraz złożony są zapisywane w postaci zamknięte.  
  
|Pascal|Formatu|nie|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a>Uwzględniana wielkość liter  
 Języki, które można uruchamiać na CLR są nie muszą obsługiwać uwzględnianie wielkości liter, mimo że niektóre czy. Nawet jeśli język obsługuje tę funkcję, innych języków, które mogą uzyskiwać dostęp do Twojego framework nie. Wszystkie interfejsy API, które są dostępne z zewnątrz, w związku z tym nie zależą od wielkości liter, samodzielnie, aby rozróżnić dwóch nazw w tym samym kontekście.  
  
 **X nie** założono, że wszystkie języki programowania jest uwzględniana wielkość liter. Nie są one. Nazwy nie mogą się różnić w przypadku samodzielnie.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
