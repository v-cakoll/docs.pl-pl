---
title: Przeciążenia operatorów
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ca42d25a5f3456c6a10eff76d7015656322abae
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192473"
---
# <a name="operator-overloads"></a>Przeciążenia operatorów
Przeciążenia operatorów zezwala na typy framework są wyświetlane tak, jakby były one elementów podstawowych języka wbudowanych.  
  
 Mimo że dozwolonych i przydatne w niektórych sytuacjach przeciążenia operatorów powinny być używane ostrożnie. Istnieje wiele przypadków, w której operator przeciążenia ma zostały użyte, takie jak podczas uruchamiania projektantów framework można używać operatorów dla operacji, które powinny być proste metody. Poniższe wskazówki powinien pomóc zdecydować, kiedy i jak użycie przeładowania operatora.  
  
 **X AVOID** Definiowanie przeciążenia operatora w typów, które powinny uznać, takich jak typy pierwotne (wbudowane).  
  
 **✓ CONSIDER** Definiowanie przeciążenia operatora w typie, który powinien uznać, takie jak typ pierwotny.  
  
 Na przykład <xref:System.String?displayProperty=nameWithType> ma `operator==` i `operator!=` zdefiniowane.  
  
 **✓ DO** definiować przeciążeń operatora w strukturach, które reprezentują numery (takie jak <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** można cute podczas definiowania przeciążenia operatora.  
  
 Przeciążanie operatora jest przydatne w sytuacjach, w których jest od razu widoczne jaki będzie wynik operacji. Na przykład, dobrym pomysłem będzie mieć możliwość odjęcie jednego <xref:System.DateTime> z innego `DateTime` i Uzyskaj <xref:System.TimeSpan>. Jednak nie jest odpowiedni do użycia logiczny operator union, union zapytań dwie bazy danych lub użyć operator przesunięcia bitowego do zapisywania do strumienia.  
  
 **X DO NOT** Podaj operator overloads, chyba że jest co najmniej jeden z argumentów typu Definiowanie przeciążenia.  
  
 **✓ DO** przeciążać operatory w sposób symetrycznego.  
  
 Na przykład, jeśli przeładujesz `operator==`, powinien także przeciążać `operator!=`. Podobnie jeśli przeładujesz `operator<`, powinien także przeciążać `operator>`i tak dalej.  
  
 **✓ CONSIDER** zapewniając metod przyjaznych nazw, które odpowiadają do każdego przeciążonego operatora.  
  
 Wiele języków nie obsługują przeciążanie operatora. Z tego powodu zaleca się, że typy, które przeciążają operatory obejmują metody pomocniczej z odpowiednią nazwę specyficznego dla domeny, która zapewnia podobne funkcje.  
  
 Poniższa tabela zawiera listę operatorów i odpowiadających im nazw przyjaznych metody.  
  
|Symbol operatora w języku C#|Nazwa metadanych|Przyjazna nazwa|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a>Przeciążanie operatora ==  
 Przeciążanie `operator ==` jest dość skomplikowane. Semantyki operatora muszą być zgodne z kilku innych członków, takich jak <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operatory konwersji  
 Operatory konwersji są operatory jednoargumentowe, które umożliwiają konwersja z jednego typu na inny. Operatory muszą być zdefiniowane jako elementy statyczne argument lub zwracany typ. Istnieją dwa typy operatory konwersji: jawne i niejawne.  
  
 **X DO NOT** Podaj operatora konwersji, jeśli takie konwersja nie jest wyraźnie oczekiwany przez użytkowników końcowych.  
  
 **X DO NOT** definiować operatory konwersji poza domeny typu.  
  
 Na przykład <xref:System.Int32>, <xref:System.Double>, i <xref:System.Decimal> są wszystkie typy liczbowe, podczas gdy <xref:System.DateTime> nie jest. Dlatego powinny być żaden operator konwersji, aby przekonwertować `Double(long)` do `DateTime`. W takim przypadku jest preferowane konstruktora.  
  
 **X DO NOT** Podaj operator niejawnej konwersji, jeśli konwersja jest potencjalnie stratnej.  
  
 Na przykład, nie powinno być niejawna konwersja z `Double` do `Int32` ponieważ `Double` zapewnia szerszy zakres niż `Int32`. Operator jawnej konwersji można podać, nawet jeśli konwersja jest potencjalnie stratnej.  
  
 **X DO NOT** zgłaszanie wyjątków z niejawnego rzutowania.  
  
 Jest to bardzo trudne dla użytkowników końcowych zorientować się, ponieważ nie są świadomi, że konwersja jest wykonywana.  
  
 **✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> jeśli powoduje wywołanie operatora rzutowania stratnej konwersji i kontrakt operator nie zezwala stratnej konwersji.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
