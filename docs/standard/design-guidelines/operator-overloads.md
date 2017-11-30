---
title: "Przeciążenia operatorów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffd472a7c410bd541ea0382f05f7ed92acb0e688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="operator-overloads"></a>Przeciążenia operatorów
Przeciążenia operatorów Zezwalaj typy framework się tak, jakby były w nim elementów podstawowych języka wbudowanych.  
  
 Dozwolone i w niektórych sytuacjach przydatne, przeciążenia operatora należy używać ostrożnie. Istnieje wiele przypadków, w którym operator przeładowanie ma zostały użyte, takich jak uruchomienia framework Designer na operatory dla operacji, które powinny być proste metody. Poniższe wskazówki powinny pomóc w określeniu, kiedy i jak użycie przeładowania operatora.  
  
 **X należy UNIKAĆ** Definiowanie przeciążenia operatora w typów, które powinny uznać, takich jak typy pierwotne (wbudowane).  
  
 **ROZWAŻ ✓** Definiowanie przeciążenia operatora w typie, który powinien uznać, takie jak typ pierwotny.  
  
 Na przykład <xref:System.String?displayProperty=nameWithType> ma `operator==` i `operator!=` zdefiniowane.  
  
 **CZY ✓** definiować przeciążeń operatora w strukturach, które reprezentują numery (takie jak <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X nie** można cute podczas definiowania przeciążenia operatora.  
  
 Przeładowanie operatora jest przydatne w sytuacjach, w których jest od razu widoczne co wynik operacji będzie. Na przykład, warto mieć możliwość odjąć jedną <xref:System.DateTime> z innego `DateTime` i uzyskać <xref:System.TimeSpan>. Jednak nie jest odpowiedni, użyj logicznego operator union, union kwerend dwie bazy danych lub użyj operatora shift, aby zapisać do strumienia.  
  
 **X nie** Podaj operator overloads, chyba że jest co najmniej jeden z argumentów typu Definiowanie przeciążenia.  
  
 **CZY ✓** przeciążać operatory w sposób symetrycznego.  
  
 Na przykład, jeśli można przeciążać `operator==`, powinien także przeciążać `operator!=`. Podobnie jeśli można przeciążać `operator<`, powinien także przeciążać `operator>`i tak dalej.  
  
 **ROZWAŻ ✓** zapewniając metod przyjaznych nazw, które odpowiadają do każdego przeciążonego operatora.  
  
 Przeładowanie operatora nie obsługują wiele języków. Z tego powodu zaleca się, że typy, które przeciążać operatory obejmuje dodatkowej metody z odpowiednią nazwę specyficznego dla domeny, która udostępnia podobne funkcje.  
  
 Poniższa tabela zawiera listę operatory i metody przyjaznej nazwy.  
  
|Symbol operatora C#|Nazwa metadanych|Przyjazna nazwa|  
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
 Przeciążanie `operator ==` jest dość złożone. Semantyka operatora musi być zgodna z kilku innych elementach członkowskich, takich jak <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operatory konwersji  
 Operatory konwersji są operatory jednoargumentowe, umożliwiających konwersja z typu na inny. Operatory musi być zdefiniowany jako statyczne elementy członkowskie na argument lub typ zwracany. Istnieją dwa typy operatory konwersji: jawne i niejawne.  
  
 **X nie** Podaj operatora konwersji, jeśli takie konwersja nie jest wyraźnie oczekiwany przez użytkowników końcowych.  
  
 **X nie** definiować operatory konwersji poza domeny typu.  
  
 Na przykład <xref:System.Int32>, <xref:System.Double>, i <xref:System.Decimal> są wszystkie typy liczbowe, podczas gdy <xref:System.DateTime> nie jest. W związku z tym nie powinny istnieć żaden operator konwersji, aby przekonwertować `Double(long)` do `DateTime`. W takim przypadku jest preferowane konstruktora.  
  
 **X nie** Podaj operator niejawnej konwersji, jeśli konwersja jest potencjalnie stratnej.  
  
 Na przykład nie należy niejawna konwersja z `Double` do `Int32` ponieważ `Double` ma większej niż `Int32`. Operator jawnej konwersji można podać, nawet jeśli konwersja jest potencjalnie stratnej.  
  
 **X nie** zgłaszanie wyjątków z niejawnego rzutowania.  
  
 Jest bardzo trudne dla użytkowników końcowych zorientować się, ponieważ nie może być należy pamiętać, że konwersja jest wykonywana.  
  
 **CZY ✓** throw <xref:System.InvalidCastException?displayProperty=nameWithType> jeśli powoduje wywołanie operatora rzutowania stratnej konwersji i kontrakt operator nie zezwala stratnej konwersji.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania elementu członkowskiego](../../../docs/standard/design-guidelines/member.md)  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)
