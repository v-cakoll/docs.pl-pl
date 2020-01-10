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
ms.openlocfilehash: fee7f5b7749c97a87e37581f67cbe1b49250b9ce
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709533"
---
# <a name="capitalization-conventions"></a>Konwencje dotyczące wielkości liter
Wytyczne w tym rozdziale określają prostą metodę używania przypadku, która jest stosowana spójnie, dzięki czemu identyfikatory typów, elementów członkowskich i parametrów łatwo odczytać.  
  
## <a name="capitalization-rules-for-identifiers"></a>Reguły dotyczące wersalików dla identyfikatorów  
 Aby rozróżnić słowa w identyfikatorze, należy zrobić wielką literę każdego wyrazu w identyfikatorze. Nie należy używać podkreśleń do rozróżniania wyrazów lub dla tego znaczenia, gdziekolwiek w identyfikatorach. Istnieją dwa odpowiednie sposoby na wielkie litery, w zależności od użycia identyfikatora:  
  
- PascalCasing  
  
- camelCasing  
  
 Konwencja PascalCasing używana dla wszystkich identyfikatorów z wyjątkiem nazw parametrów, wielką literą w pierwszym znaku każdego wyrazu (w tym akronimów przez dwie litery), jak pokazano w następujących przykładach:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Szczególny przypadek jest tworzony w przypadku dwuliterowych akronimów, w których obie litery są pisane wielkimi literami, jak pokazano w poniższym identyfikatorze:  
  
 `IOStream`  
  
 Konwencja camelCasing używana tylko w przypadku nazw parametrów, wielką literą pierwszego znaku każdego wyrazu, z wyjątkiem pierwszego wyrazu, jak pokazano w poniższych przykładach. Jak widać również przykład, dwuliterowe akronimy, które rozpoczynają notacji CamelCase identyfikator, są zarówno małymi literami.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** Użyj PascalCasing dla wszystkich publicznych nazw elementu członkowskiego, typ i przestrzeń nazw składającą się z wielu wyrazów.  
  
 **✓ DO** camelCasing na użytek nazwy parametrów.  
  
 W poniższej tabeli opisano reguły dotyczące wielkich liter dla różnych typów identyfikatorów.  
  
|Identyfikator|Wielkość znaków|Przykład|  
|----------------|------------|-------------|  
|Przestrzeń nazw|Pascal|`namespace System.Security { ... }`|  
|Typ|Pascal|`public class StreamReader { ... }`|  
|Interfejs|Pascal|`public interface IEnumerable { ... }`|  
|Metoda|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Właściwość|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Zdarzenie|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Pole|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Wartość wyliczenia|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parametr|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Wielkie litery słów i typowe terminy  
 Większość postanowień złożonych jest traktowanych jako pojedyncze słowa do celów wielkich liter.  
  
 **X DO NOT** własne w tzw wyrazy złożone zamknąć formularz.  
  
 Są to wyrazy złożone zapisywane jako pojedyncze słowo, takie jak punkt końcowy. Aby zapoznać się z wytycznymi dotyczącymi wielkości liter, Traktuj zamknięty wyraz złożony jako pojedynczy wyraz. Użyj bieżącego słownika, aby określić, czy złożone słowo jest zapisywana w zamkniętym formularzu.  
  
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
 Języki, które mogą być uruchamiane w środowisku CLR, nie są wymagane do obsługi rozróżniania wielkości liter, chociaż niektóre z nich wykonują. Nawet jeśli język obsługuje tę funkcję, inne języki, które mogą uzyskać dostęp do platformy, nie. Wszystkie interfejsy API, które są dostępne z zewnątrz, w związku z tym nie mogą polegać na przypadku odróżnienia dwóch nazw w tym samym kontekście.  
  
 **X DO NOT** założono, że wszystkie języki programowania jest uwzględniana wielkość liter. Nie są. Nazwy nie mogą różnić się w zależności od wielkości liter.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
