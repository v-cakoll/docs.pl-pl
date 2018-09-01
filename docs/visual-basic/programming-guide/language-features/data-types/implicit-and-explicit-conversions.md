---
title: Konwersje jawne i niejawne (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 09d96b304ba3bcf2a9de2812ce37ae69dba73a41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396597"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Konwersje jawne i niejawne (Visual Basic)
*Niejawna konwersja* nie wymaga żadnych specjalnej składni w kodzie źródłowym. W poniższym przykładzie Visual Basic niejawnie konwertuje wartość `k` na wartość zmiennoprzecinkową o pojedynczej dokładności przed przypisaniem go do `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *Jawną konwersję* używa słowa kluczowego konwersji typu. Visual Basic oferuje kilka takich słowa kluczowe, które coerce — wyrażenia w nawiasach do danych żądanego typu. Te słowa kluczowe zachowywać się jak functions, ale kompilator generuje kod inline, dzięki czemu wykonanie jest nieznacznie wyższa niż w przypadku wywołania funkcji.  
  
 Następujące rozszerzenia powyższego przykładu `CInt` — słowo kluczowe konwertuje wartość `q` do liczby całkowitej przed przypisaniem go do `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 W poniższej tabeli przedstawiono słowa kluczowe konwersji dostępne.  
  
|Konwersja typu — słowo kluczowe|Konwertuje wyrażenie na typ danych|Typy danych wyrażenia, które ma zostać przekonwertowany|  
|---|---|---|  
|`CBool`|[Boolean, typ danych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `String`, `Object`|  
|`CByte`|[Byte, typ danych](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Dowolnego typu liczbowego (w tym `SByte` i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CChar`|[Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date, typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double, typ danych](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CDec`|[Decimal, typ danych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CInt`|[Integer, typ danych](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CLng`|[Long, typ danych](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CObj`|[Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Dowolnego typu|  
|`CSByte`|[SByte, typ danych](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Dowolnego typu liczbowego (w tym `Byte` i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CShort`|[Short, typ danych](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CSng`|[Single, typ danych](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CStr`|[String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `Char`, `Char` tablicy, `Date`, `Object`|  
|`CType`|Określony typ po przecinku (`,`)|Podczas konwertowania na *typu danych podstawowych* (łącznie z tablicy typu podstawowego) typy takie same jak dozwolone dla odpowiedniej konwersji — słowo kluczowe<br /><br /> Podczas konwertowania na *złożonego typu danych*, interfejsy implementuje i klasy, z których dziedziczy<br /><br /> Podczas konwertowania na klasy lub struktury, na którym przeciążają `CType`, tej klasy lub struktury|  
|`CUInt`|[UInteger, typ danych](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CULng`|[ULong, typ danych](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
|`CUShort`|[UShort, typ danych](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Dowolnego typu liczbowego (w tym `Byte`, `SByte`i są wyliczone typów), `Boolean`, `String`, `Object`|  
  
## <a name="the-ctype-function"></a>CType — funkcja  
 [Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) działa na dwóch argumentów. Pierwszy jest wyrażeniem, które ma zostać przekonwertowany, a drugą jest wartość klasy docelowej danych typu lub obiektu. Należy pamiętać, że pierwszy argument musi być wyrażeniem, nie typu.  
  
 `CType` jest *funkcja śródwierszowa*, co oznacza skompilowany kod sprawia, że konwersja, często bez generowania funkcję wywołania. Poprawia to wydajność.  
  
 Porównanie `CType` przy użyciu innych typów słowa kluczowe konwersji, zobacz [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) i [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Typy podstawowe  
 W poniższym przykładzie pokazano użycie `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Typy złożone  
 Możesz użyć `CType` można przekonwertować wartości na złożone typy danych jak również do typów podstawowych. Można również użyć do zmuszania klasy obiektu na typ jednego z jego interfejsów, jak w poniższym przykładzie.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Typy tablic  
 `CType` można także przekonwertować typy danych tablicy, jak w poniższym przykładzie.  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [konwersje tablicę](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### <a name="types-defining-ctype"></a>Typy Definiowanie CType  
 Można zdefiniować `CType` dla klasy lub struktury, które zostały zdefiniowane. Dzięki temu można przekonwertować wartości do i z typu klasy lub struktury. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [porady: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Wartości używane ze słowem kluczowym konwersji muszą być prawidłowe dla docelowego typu danych lub wystąpienia błędu. Na przykład, jeśli użytkownik spróbuje przekonwertować `Long` do `Integer`, wartość `Long` należy do prawidłowego zakresu dla `Integer` typu danych.  
  
> [!CAUTION]
>  Określanie `CType` umożliwia przekonwertowanie z jedną klasę do innego kończy się niepowodzeniem w czasie wykonywania, jeśli typ źródłowy nie pochodzi od typu miejsca docelowego. Taka awaria zgłasza <xref:System.InvalidCastException> wyjątku.  
  
 Jednak jeśli jeden z typów struktury lub klasy, które zostały zdefiniowane i zdefiniowaniu `CType` dla tej struktury lub klasy, konwersja może powieść, jeśli spełnia on wymagania Twojej `CType`. Zobacz [porady: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Wykonywania konwersji jawnej jest także znana jako *rzutowania* wyrażenia klasy danych danego typu lub obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Konwertowanie między ciągami a innymi typami danych](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Porady: konwertowanie obiektu na inny typ w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
