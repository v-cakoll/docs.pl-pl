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
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837275"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Typy wbudowane dla wspólnych elementów podstawowych języka XAML
XAML 2009 wprowadza obsługę poziomu języka XAML dla kilku typów danych, które są często używane jako elementy pierwotne w środowisku uruchomieniowym języka wspólnego (CLR) i w innych językach programowania. Język XAML 2009 dodaje obsługę następujących elementów podstawowych: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`i `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Poprzednie techniki dla elementów podstawowych języka w znacznikach języka XAML  
 W języku XAML dla wcześniejszych wersji środowiska WPF można odwoływać się do elementów podstawowych języka środowiska CLR przez mapowanie zestawu i przestrzeni nazw zawierających klasę definicji elementu podstawowego środowiska CLR dla środowiska .NET Framework. Większość z nich znajduje się w zestawie mscorlib i obszarze nazw <xref:System>. Na przykład aby użyć typu <xref:System.Int32>, można zadeklarować następujące mapowanie (z przykładem w dalszej części):  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>Funkcje pierwotne XAML 2009  
 Umownie wyświetlane są pierwotne wartości języka XAML i wszystkie inne elementy języka XAML, łącznie z prefiksem `x:`. W ten sposób elementy języka XAML są zwykle używane w znacznikach rzeczywistych. W dokumentacji koncepcyjnej XAML w programie WPF, a także w specyfikacji języka XAML występuje niniejsza konwencja.  
  
### <a name="xobject"></a>x:Object  
 Dla obsługi środowiska CLR element podstawowy `x:Object` odpowiada obiektowi <xref:System.Object>.  
  
 Ten typ pierwotny nie jest zazwyczaj używany w zaznaczaniu aplikacji, ale może być pomocny w niektórych scenariuszach, takich jak sprawdzanie zbywalności w systemie typu XAML.  
  
### <a name="xboolean"></a>x:Boolean  
 Dla obsługi środowiska CLR element podstawowy `x:Boolean` odpowiada obiektowi <xref:System.Boolean>.  
  
 XAML analizuje wartości dla `x:Boolean` bez uwzględniania wielkości liter. Należy zauważyć, że obiekt `x:Bool` nie jest alternatywą zaakceptowaną. Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.17 i 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xchar"></a>x:Char  
 Dla obsługi środowiska CLR element podstawowy `x:Char` odpowiada obiektowi <xref:System.Char>.  
  
 Typy String lub char wchodzą w interakcję z ogólnym kodowaniem pliku na poziomie XML. Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.7 i 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xstring"></a>x:String  
 Dla obsługi środowiska CLR element podstawowy `x:String` odpowiada obiektowi <xref:System.String>.  
  
 Typy String lub char wchodzą w interakcję z ogólnym kodowaniem pliku na poziomie XML. Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdecimal"></a>x:Decimal  
 Dla obsługi środowiska CLR element podstawowy `x:Decimal` odpowiada obiektowi <xref:System.Decimal>.  
  
 Należy zauważyć, że analiza składni języka XAML standardowo odbywa się w kulturze `en-US`. W kulturze `en-US`, poprawnym separatorem dla elementów ułamków dziesiętny jest zawsze kropka (`.`) niezależnie od ustawień kultury środowiska programowania lub obiektu docelowego ewentualnego klienta gdzie plik XAML jest ładowany w czasie wykonywania.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.14 i 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xsingle"></a>x:Single  
 Dla obsługi środowiska CLR element podstawowy `x:Single` odpowiada obiektowi <xref:System.Single>.  
  
 Oprócz wartości liczbowych składnia tekstu `x:Single` również pozwala na tokeny `Infinity`, `-Infinity` i `NaN`. Te tokeny uwzględniają wielkość liter.  
  
 `x:Single` może obsługiwać wartości w postaci notacji naukowej, jeśli pierwszy znak w składni tekstu to `e` lub `E`.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.8 i 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdouble"></a>x:Double  
 Dla obsługi środowiska CLR element podstawowy `x:Double` odpowiada obiektowi <xref:System.Double>.  
  
 Oprócz wartości liczbowych składnia tekstu `x:Double` pozwala na tokeny `Infinity`, `-Infinity` i `NaN`. Te tokeny uwzględniają wielkość liter.  
  
 `x:Double` może obsługiwać wartości w postaci notacji naukowej. Użyj znaku `e` lub `E` do wprowadzenia wykładnika.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.9 i 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint16"></a>x:Int16  
 Dla obsługi środowiska CLR element podstawowy `x:Int16` odpowiada obiektowi <xref:System.Int16> i element podstawowy `x:Int16` jest traktowany jako podpisany. W języku XAML brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.11 i 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint32"></a>x:Int32  
 Dla obsługi środowiska CLR element podstawowy `x:Int32` odpowiada obiektowi <xref:System.Int32>. `x:Int32` jest traktowany jako oznaczony. W języku XAML brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.12 i 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint64"></a>x:Int64  
 Dla obsługi środowiska CLR element podstawowy `x:Int64` odpowiada obiektowi <xref:System.Int64>. `x:Int64` jest traktowany jako oznaczony. W języku XAML brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.13 i 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 Dla obsługi środowiska CLR element podstawowy `x:TimeSpan` odpowiada obiektowi <xref:System.TimeSpan>.  
  
 Należy zauważyć, że analiza składni języka XAML pod kątem formatu daty i godziny standardowo odbywa się w kulturze `en-US`.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.16 i 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xuri"></a>x:Uri  
 Dla obsługi środowiska CLR element podstawowy `x:Uri` odpowiada obiektowi <xref:System.Uri>.  
  
 Szukanie protokołów nie jest częścią definicji XAML dla `x:Uri`.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.15 i 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xbyte"></a>x:Byte  
 Dla obsługi środowiska CLR element podstawowy `x:Byte` odpowiada obiektowi <xref:System.Byte>. <xref:System.Byte> / `x:Byte` jest traktowana jako niepodpisana.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [\[MS-XAML\] sekcje 5.2.10 i 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xarray"></a>x:Array  
 Dla obsługi środowiska CLR element podstawowy `x:Array` odpowiada obiektowi <xref:System.Array>.  
  
 Można zdefiniować tablicę w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; Jednak składnia XAML 2009 jest zdefiniowaną przez język podstawową, która nie wymaga dostępu do rozszerzenia znacznika. Aby uzyskać więcej informacji na temat obsługi języka XAML 2006, zobacz [X:Array Markup Extension](x-array-markup-extension.md).  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz sekcję [\[MS-XAML\] sekcjach 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Obsługa WPF  
 W programie WPF można używać funkcji języka XAML 2009, ale tylko dla języka XAML, który nie jest kompilowany do znaczników. Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.  
  
 Scenariusz, w którym można używać funkcji języka XAML 2009 razem z WPF, to jeśli utworzysz luźny kod XAML, a następnie załadujesz ten kod XAML do środowiska uruchomieniowego WPF i grafu obiektów z <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF i jej <xref:System.Windows.Markup.XamlReader.Load%2A> mogą przetwarzać słowa kluczowe języka XAML 2009 i funkcje do prawidłowej reprezentacji grafu obiektów.
