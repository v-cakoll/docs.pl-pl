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
ms.openlocfilehash: f6225dfcc02b90da58ccafd5c70726b6f80f29d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731355"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Typy wbudowane dla wspólnych elementów podstawowych języka XAML
XAML 2009 wprowadza wsparcie poziomu języka XAML dla kilku typów danych, które są często używanymi wartościami pierwotnymi w środowisku uruchomieniowym języka (wspólnego CLR) i w innych językach programowania. XAML 2009 dodaje obsługę tych wartości pierwotnych: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, i `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Poprzednie techniki dla elementów podstawowych języka w znaczniku XAML  
 W XAML dla wcześniejszych wersji środowiska WPF mapowanie zestawu i przestrzeni nazw zawierających klasę definicji elementu podstawowego środowiska CLR programu .NET Framework mogą odwoływać się do elementów podstawowych języka środowiska CLR. Większość z nich znajdują się w zestawie mscorlib i <xref:System> przestrzeni nazw. Na przykład, aby użyć <xref:System.Int32>, można zadeklarować następujące mapowanie (z przykładem później):  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>XAML 2009 — elementów podstawowych języka  
 Umownie wyświetlane są pierwotne wartości języka XAML i wszystkie inne elementy języka XAML, w tym `x:` prefiks. Jest to, jak elementy języka XAML są zwykle używane w znacznikach rzeczywistych. Występuje Niniejsza Konwencja w dokumentacji koncepcyjnej XAML w WPF, a także w specyfikacji XAML.  
  
### <a name="xobject"></a>x: obiekt  
 Dla obsługi środowiska CLR `x:Object` podstawowego odnosi się do <xref:System.Object>.  
  
 Ten typ pierwotny nie jest zazwyczaj używany w zaznaczaniu aplikacji, ale może być pomocny w niektórych scenariuszach, takich jak sprawdzanie zbywalności w systemie typu XAML.  
  
### <a name="xboolean"></a>x: Boolean  
 Dla obsługi środowiska CLR `x:Boolean` podstawowego odnosi się do <xref:System.Boolean>.  
  
 XAML analizuje wartości dla `x:Boolean` bez uwzględniania wielkości liter. Należy pamiętać, że `x:Bool` nie jest alternatywą zaakceptowaną. Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.17 i 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 Dla obsługi środowiska CLR `x:Char` podstawowego odnosi się do <xref:System.Char>.  
  
 Typy String lub char wchodzą mają interakcję z ogólnym kodowaniem pliku na poziomie XML. Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.7 i 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: String.  
 Dla obsługi środowiska CLR `x:String` podstawowego odnosi się do <xref:System.String>.  
  
 Typy String lub char wchodzą mają interakcję z ogólnym kodowaniem pliku na poziomie XML. Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcja 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: dziesiętne  
 Dla obsługi środowiska CLR `x:Decimal` podstawowego odnosi się do <xref:System.Decimal>.  
  
 Należy pamiętać, że analiza kodu XAML standardowo odbywa się w obszarze `en-US` kultury. W obszarze `en-US` kultury, poprawnym separatorem dla elementów ułamków dziesiętny jest zawsze kropka (`.`) niezależnie od ustawień kultury środowiska programowania lub obiektu docelowego ewentualnego klienta gdzie XAML jest ładowany w czasie wykonywania.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.14 i 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: Single  
 Dla obsługi środowiska CLR `x:Single` podstawowego odnosi się do <xref:System.Single>.  
  
 Oprócz wartości liczbowych składnia tekstu `x:Single` również pozwala na tokeny `Infinity`, `-Infinity`, i `NaN`. Te tokeny uwzględniają wielkość liter.  
  
 `x:Single` może obsługiwać wartości w postaci notacji naukowej, jeśli pierwszy znak w składni tekstu to `e` lub `E`.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.8 i 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: Double  
 Dla obsługi środowiska CLR `x:Double` podstawowego odnosi się do <xref:System.Double>.  
  
 Oprócz wartości liczbowych składnia tekstu `x:Double` pozwala na tokeny `Infinity`, `-Infinity`, i `NaN`. Te tokeny uwzględniają wielkość liter.  
  
 `x:Double` może obsługiwać wartości w postaci notacji naukowej. Użyj znaku `e` lub `E` do wprowadzenia wykładnika.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.9 i 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16.  
 Dla obsługi środowiska CLR `x:Int16` podstawowego odnosi się do <xref:System.Int16> i `x:Int16` jest traktowany jako podpisany. W XAML, Brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.11 i 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x: Int32  
 Dla obsługi środowiska CLR `x:Int32` podstawowego odnosi się do <xref:System.Int32>. `x:Int32` jest traktowany jako podpisany. W XAML, Brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.12 i 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64.  
 Dla obsługi środowiska CLR `x:Int64` podstawowego odnosi się do <xref:System.Int64>. `x:Int64` jest traktowany jako podpisany. W XAML, Brak znaku plusa (`+`) w składni tekstu jest przez domniemanie interpretowany jako wartość ze znakiem dodatnim.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.13 i 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x: TimeSpan  
 Dla obsługi środowiska CLR `x:TimeSpan` podstawowego odnosi się do <xref:System.TimeSpan>.  
  
 Pamiętaj, że analiza kodu XAML formatu daty i godziny standardowo odbywa się w obszarze `en-US` kultury.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.16 i 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: Uri  
 Dla obsługi środowiska CLR `x:Uri` podstawowego odnosi się do <xref:System.Uri>.  
  
 Szukanie protokołów nie jest częścią definicji XAML dla `x:Uri`.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.15 i 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: Byte  
 Dla obsługi środowiska CLR `x:Byte` podstawowego odnosi się do <xref:System.Byte>. A <xref:System.Byte>  /  `x:Byte` jest traktowany jako nieoznaczony.  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcje 5.2.10 i 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x: Array  
 Dla obsługi środowiska CLR `x:Array` podstawowego odnosi się do <xref:System.Array>.  
  
 Można zdefiniować tablicę w XAML 2006 za pomocą składni rozszerzenia znaczników; Składnia XAML 2009 jest jednak zdefiniowanym przez język podstawowy, który nie wymaga dostępu do rozszerzenia znacznika. Aby uzyskać więcej informacji na temat obsługi XAML 2006, zobacz [x: Array — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Aby uzyskać definicję specyfikacji języka XAML, zobacz [ \[MS-XAML\] sekcja 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Obsługa platformy WPF  
 W środowisku WPF można użyć funkcji XAML 2009, ale tylko dla XAML, która nie jest kompilowana do znaczników. XAML kompilowana do znaczników dla platformy WPF i formularz BAML XAML aktualnie nie obsługują tych funkcji i słowa kluczowe XAML 2009.  
  
 Scenariusz, w którym można korzystać z funkcji XAML 2009 z WPF jest, jeśli autor luźne XAML, a następnie załadować tej XAML w WPF środowiska uruchomieniowego i wykres obiektu z <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> i jego <xref:System.Windows.Markup.XamlReader.Load%2A> może przetwarzać słowa kluczowe języka XAML 2009 oraz funkcje do prawidłowego obiektu reprezentującego wykres.
