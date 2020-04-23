---
title: Typy wbudowane dla wspólnych elementów podstawowych języka XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071837"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Wbudowane typy dla wspólnych elementów pierwotnych języka XAML

XAML 2009 wprowadza obsługę języka XAML dla kilku typów danych, które są często używane prymitywy w czasie wykonywania języka wspólnego (CLR) i w innych językach programowania. XAML 2009 `x:Object`dodaje obsługę tych prymitywów: `x:Single` `x:Double`, `x:Int16` `x:Boolean` `x:Int32`, `x:Int64` `x:Char` `x:TimeSpan`, `x:Uri` `x:String`, `x:Decimal`, , , , , , , , , , `x:Byte`, i`x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Poprzednie techniki ujednolicenia języka w znacznikach XAML

 W XAML dla poprzednich wersji WPF można odwoływać się do ćwierczy języka CLR mapując zestawu i przestrzeni nazw, które zawierały klasę definicji pierwotnej CLR dla programu .NET Framework. Większość z nich znajduje się w <xref:System> mscorlib zestawu i przestrzeni nazw. Na przykład, <xref:System.Int32>aby użyć , można zadeklarować następujące mapowanie (z przykładowym użyciem pokazanym później):

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>Podstawowe wersje językowe XAML 2009

Zgodnie z konwencją są wyświetlane prymitywy języka dla języka XAML `x:` i wszystkie inne elementy języka XAML, w tym prefiks. W ten sposób elementy języka XAML są zwykle używane w rzeczywistych znaczników. Ta konwencja jest stosowana w dokumentacji koncepcyjnej dla XAML w WPF, a także w specyfikacji XAML.

### <a name="xobject"></a>x:Obiekt

W przypadku podkładu `x:Object` CLR prymityw odpowiada <xref:System.Object>.

Ten pierwotny nie jest zwykle używany w znacznikach aplikacji, ale może być przydatne w niektórych scenariuszach, takich jak sprawdzanie możliwości przypisania w systemie typu XAML.

### <a name="xboolean"></a>x:Wartość logiczna

W przypadku podkładu `x:Boolean` CLR prymityw odpowiada <xref:System.Boolean>.

XAML analizuje wartości `x:Boolean` jako bez uwzględniania wielkości liter. Należy `x:Bool` pamiętać, że nie jest akceptowaną alternatywą. Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.17 i 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xchar"></a>x:Znak

W przypadku podkładu `x:Char` CLR prymityw odpowiada <xref:System.Char>.

Typy ciągów i znaków mają interakcję z ogólnym kodowaniem pliku na poziomie XML. Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.7 i 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xstring"></a>x:Ciąg znaków

W przypadku podkładu `x:String` CLR prymityw odpowiada <xref:System.String>.

Typy ciągów i znaków mają interakcję z ogólnym kodowaniem pliku na poziomie XML. Definicja specyfikacji języka XAML umożliwia [ \[opisanie sekcji\] MS-XAML 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdecimal"></a>x:Dziesiętne

W przypadku podkładu `x:Decimal` CLR prymityw odpowiada <xref:System.Decimal>.

Analizowanie XAML jest z `en-US` natury wykonywane w ramach kultury. W `en-US` obszarze kultura poprawny separator dla składników dziesiętnych`.`jest zawsze kropka ( ) niezależnie od ustawień kultury środowiska deweloperskiego lub ostatecznego celu klienta, w którym XAML jest ładowany w czasie wykonywania.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.14 i 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xsingle"></a>x:Pojedynczy

W przypadku podkładu `x:Single` CLR prymityw odpowiada <xref:System.Single>.

Oprócz wartości liczbowych składnia tekstu zezwala `x:Single` również na `Infinity`tokeny `-Infinity` `NaN`, i . Te tokeny są traktowane jako rozróżniane wielkość liter.

`x:Single`może obsługiwać wartości w formie notacji naukowej, jeśli `e` `E`pierwszy znak w składni tekstu jest lub .

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.8 i 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdouble"></a>x:Podwójne

W przypadku podkładu `x:Double` CLR prymityw odpowiada <xref:System.Double>.

Oprócz wartości liczbowych składnia tekstu zezwala `x:Double` na `Infinity`tokeny `-Infinity`, `NaN`i . Te tokeny są traktowane jako rozróżniane wielkość liter.

`x:Double`może obsługiwać wartości w formie notacji naukowej. Użyj znaku `e` `E` lub wprowadzić część wykładniczą.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.9 i 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint16"></a>x:Int16

W przypadku kopii `x:Int16` CLR wartość pierwotna odpowiada <xref:System.Int16> i `x:Int16` jest traktowana jako podpisana. W języku XAML brak składni tekstu plus (`+`) jest implikowany jako wartość podpisana dodatnia.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.11 i 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint32"></a>x:Int32

W przypadku podkładu `x:Int32` CLR prymityw odpowiada <xref:System.Int32>. `x:Int32`traktowane jako podpisane. W języku XAML brak składni tekstu plus (`+`) jest implikowany jako wartość podpisana dodatnia.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.12 i 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint64"></a>x:Int64

W przypadku podkładu `x:Int64` CLR prymityw odpowiada <xref:System.Int64>. `x:Int64`traktowane jako podpisane. W języku XAML brak składni tekstu plus (`+`) jest implikowany jako wartość podpisana dodatnia.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.13 i 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xtimespan"></a>x:TimeSpan

W przypadku podkładu `x:TimeSpan` CLR prymityw odpowiada <xref:System.TimeSpan>.

Analizowanie XAML dla formatu daty czasu `en-US` jest z natury wykonywane w ramach kultury.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje MS-XAML\] 5.2.16 i 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xuri"></a>x:Uri

W przypadku podkładu `x:Uri` CLR prymityw odpowiada <xref:System.Uri>.

Sprawdzanie protokołów nie jest częścią definicji XAML dla `x:Uri`.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.15 i 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xbyte"></a>x:Bajt

W przypadku podkładu `x:Byte` CLR prymityw odpowiada <xref:System.Byte>. <xref:System.Byte>  /  A `x:Byte` jest traktowany jako niepodpisany.

Definicja specyfikacji języka XAML umożliwia szczegółowe [ \[definition sekcje\] MS-XAML 5.2.10 i 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xarray"></a>x:Tablica

W przypadku podkładu `x:Array` CLR prymityw odpowiada <xref:System.Array>.

Tablicę można zdefiniować w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; jednak składnia XAML 2009 jest pierwotnym językiem zdefiniowanym przez język, który nie wymaga uzyskiwania dostępu do rozszerzenia znaczników. Aby uzyskać więcej informacji na temat obsługi protokołu XAML 2006, zobacz [x:Array Markup Extension](xarray-markup-extension.md).

Definicja specyfikacji języka XAML umożliwia [ \[opisanie rozdziałów\] 5.2.18 dotyczących języka MS-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="wpf-support"></a>Obsługa WPF

W WPF WPF można użyć XAML 2009 funkcje, ale tylko dla XAML, który nie jest skompilowany znaczników. Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.

Scenariusz, w którym można użyć funkcji XAML 2009 wraz z WPF jest, jeśli autor luźne XAML, a <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>następnie załadować ten kod XAML do środowiska uruchomieniowego WPF i wykres obiektu z . WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF <xref:System.Windows.Markup.XamlReader.Load%2A> i jego można przetwarzać XAML 2009 słowa kluczowe języka i funkcje w prawidłowej reprezentacji wykresu obiektu.
