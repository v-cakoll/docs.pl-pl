---
title: Konwencje dotyczące wielkości liter
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: KrzysztofCwalina
ms.openlocfilehash: e0da4cd747846921d170d9c07d6f1fb91dbd4ed7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615245"
---
# <a name="capitalization-conventions"></a>Konwencje dotyczące wielkości liter
Wskazówki zawarte w tym rozdziale układ w prosty sposób za pomocą sprawa, po zastosowaniu spójnie upewnij identyfikatory dla typów, elementów członkowskich i parametrów, łatwe do odczytania.  
  
## <a name="capitalization-rules-for-identifiers"></a>Reguły wielkości liter dla identyfikatorów  
 Do odróżnienia słów w identyfikatorze, wielką pierwszą literę każdego wyrazu w identyfikatorze. Nie należy używać znaków podkreślenia do odróżnienia wyrazów, lub dla tej sprawy w dowolnym miejscu w identyfikatorach. Istnieją dwa sposoby odpowiednie na wielką identyfikatorów, w zależności od tego, użyj identyfikatora:  
  
- PascalCasing  
  
- camelCasing  
  
 Konwencja PascalCasing, umożliwiający wszystkie identyfikatory z wyjątkiem nazw parametrów powoduje rozpoczynanie pierwszego znaku wystąpień poszczególnych wyrazów (w tym akronimów za pośrednictwem dwóch liter o długości), jak pokazano w poniższych przykładach:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Przypadek specjalny wysłaniu akronimów dwuliterowych, w których oba litery pod tym, jak pokazano w następującym identyfikatorem:  
  
 `IOStream`  
  
 Konwencja camelCasing, używana tylko w przypadku nazwy parametrów powoduje rozpoczynanie pierwszym znakiem każdego wyrazu, z wyjątkiem pierwszy wyraz, jak pokazano w poniższych przykładach. W przykładzie pokazano również, skrótów dwuliterowych, które zaczynają się identyfikatorem formacie camelcase są zarówno małe litery.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** Użyj PascalCasing dla wszystkich publicznych nazw elementu członkowskiego, typ i przestrzeń nazw składającą się z wielu wyrazów.  
  
 **✓ DO** camelCasing na użytek nazwy parametrów.  
  
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
|Parametr|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Wykorzystując wyrazy złożone i typowe terminy  
 Większość warunki złożone są traktowane jako pojedynczego słowa do celów wielkość liter.  
  
 **X DO NOT** własne w tzw wyrazy złożone zamknąć formularz.  
  
 Te są zapisywane jako jednego wyrazu, takie jak punkt końcowy wyrazy złożone. Na potrzeby liter dla skrótowców należy traktować wyraz złożony zamknięte formularza jako pojedynczego wyrazu. Użyj bieżącym słowniku, aby określić, wyraz złożony zostanie zapisane w postaci zamknięte.  
  
|Pascal|Camel|nie|  
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
  
## <a name="case-sensitivity"></a>Rozróżnianie wielkości liter  
 Języki, które można uruchamiać na środowisko CLR nie są wymagane do obsługi uwzględnianie wielkości liter, mimo że niektóre zrobić. Nawet wtedy, gdy język obsługuje tę funkcję, nie są inne języki, które mogą uzyskiwać dostęp do swojej platformy. Wszystkie interfejsy API, które są dostępne z zewnątrz, dlatego nie można polegać na przypadek samodzielnie, aby rozróżnić dwóch nazw, w tym samym kontekście.  
  
 **X DO NOT** założono, że wszystkie języki programowania jest uwzględniana wielkość liter. Nie są one. Nazwy nie mogą się różnić w przypadku autonomicznej.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
