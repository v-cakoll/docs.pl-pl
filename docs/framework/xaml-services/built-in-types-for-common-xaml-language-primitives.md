---
title: "Typy wbudowane dla wspólnych elementów podstawowych języka XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6052e575b62994b54799cc1af88584f433b06ff8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Typy wbudowane dla wspólnych elementów podstawowych języka XAML
XAML 2009 wprowadzono obsługę poziom języka XAML dla kilku typów danych, które są często używanych elementów podstawowych, środowisko uruchomieniowe języka wspólnego (CLR) i w innych językach programowania. XAML 2009 dodaje obsługę tych podstawowych: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, i`x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Poprzednie techniki elementów podstawowych języka w kodzie XAML  
 W języku XAML w poprzednich wersjach WPF mapowanie zestawu i przestrzeni nazw, która zawiera klasę pierwotnych definicji CLR dla programu .NET Framework może odwoływać się do elementów podstawowych języka CLR. Większość tych znajdują się w zestawie mscorlib i <xref:System> przestrzeni nazw. Na przykład, aby użyć <xref:System.Int32>, można deklaruje następującego mapowania (z użycia przykładzie pokazano później):  
  
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
## <a name="xaml-2009-language-primitives"></a>Elementy podstawowe języka XAML 2009 języka  
 Konwencja, są wyświetlane elementów podstawowych języka XAML i wszystkie inne elementy języka XAML, łącznie z `x:` prefiks. Jest to, jak elementy języka XAML są zazwyczaj używane w znaczniku rzeczywistych. Konwencja jest zachowana w dokumentacja koncepcyjna dla XAML w WPF, a także w specyfikacji języka XAML.  
  
### <a name="xobject"></a>x: obiekt  
 Dla zapasowy CLR `x:Object` pierwotnych odpowiada <xref:System.Object>.  
  
 Ten element podstawowy nie jest zazwyczaj używana w znaczniku aplikacji, ale może być przydatne w przypadku niektórych scenariuszy, takich jak sprawdzanie assignability w systemie typów języka XAML.  
  
### <a name="xboolean"></a>x: wartość logiczna  
 Dla zapasowy CLR `x:Boolean` pierwotnych odpowiada <xref:System.Boolean>.  
  
 XAML analizuje wartości `x:Boolean` jako bez uwzględniania wielkości liter. Należy pamiętać, że `x:Bool` nie jest akceptowane zamiast. Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.17 i 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 Dla zapasowy CLR `x:Char` pierwotnych odpowiada <xref:System.Char>.  
  
 Typy String lub char mieć interakcji z ogólną kodowanie plików na tym poziomie XML. Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.7 i 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: String  
 Dla zapasowy CLR `x:String` pierwotnych odpowiada <xref:System.String>.  
  
 Typy String lub char mieć interakcji z ogólną kodowanie plików na tym poziomie XML. Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: dziesiętne  
 Dla zapasowy CLR `x:Decimal` pierwotnych odpowiada <xref:System.Decimal>.  
  
 Należy pamiętać, że analiza kodu XAML z założenia odbywa się w obszarze `en-US` kultury. W obszarze `en-US` kultury, poprawnego separatora dla składników wartości dziesiętnej jest zawsze kropka (`.`) niezależnie od kultury ustawień środowiska deweloperskiego lub docelowego ostatecznego klienta załadunku XAML w czasie wykonywania.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.14 i 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: Single  
 Dla zapasowy CLR `x:Single` pierwotnych odpowiada <xref:System.Single>.  
  
 Oprócz wartości liczbowych składnię tekst `x:Single` umożliwia również tokeny `Infinity`, `-Infinity`, i `NaN`. Tokeny te są traktowane jako wielkość liter.  
  
 `x:Single`Możliwe wartości w formie wykładniczej jest pierwszy znak w składni tekstu `e` lub `E`.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.8 i 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: Double  
 Dla zapasowy CLR `x:Double` pierwotnych odpowiada <xref:System.Double>.  
  
 Oprócz wartości liczbowych składnię tekst `x:Double` pozwala na tokeny `Infinity`, `-Infinity`, i `NaN`. Tokeny te są traktowane jako wielkość liter.  
  
 `x:Double`Możliwe wartości w formie wykładniczej. Użyć znaku `e` lub `E` wprowadzenie wykładnika części.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.9 i 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16.  
 Dla zapasowy CLR `x:Int16` pierwotnych odpowiada <xref:System.Int16> i `x:Int16` jest traktowany jako podpisany. W języku XAML, Brak znaku plus (`+`) logowania w składni tekst jest domniemane jako dodatnią podpisem.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.11 i 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x: Int32  
 Dla zapasowy CLR `x:Int32` pierwotnych odpowiada <xref:System.Int32>. `x:Int32`jest traktowany jako podpisany. W języku XAML, Brak znaku plus (`+`) logowania w składni tekst jest domniemane jako dodatnią podpisem.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.12 i 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64.  
 Dla zapasowy CLR `x:Int64` pierwotnych odpowiada <xref:System.Int64>. `x:Int64`jest traktowany jako podpisany. W języku XAML, Brak znaku plus (`+`) logowania w składni tekst jest domniemane jako dodatnią podpisem.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.13 i 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x: TimeSpan  
 Dla zapasowy CLR `x:TimeSpan` pierwotnych odpowiada <xref:System.TimeSpan>.  
  
 Pamiętaj, że analiza kodu XAML na format godziny i daty z założenia odbywa się w obszarze `en-US` kultury.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.16 i 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: Uri  
 Dla zapasowy CLR `x:Uri` pierwotnych odpowiada <xref:System.Uri>.  
  
 Sprawdzanie protokołów nie jest częścią definicji XAML `x:Uri`.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje ppkt 5.2.15 i 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: Byte  
 Dla zapasowy CLR `x:Byte` pierwotnych odpowiada <xref:System.Byte>. A <xref:System.Byte>  /  `x:Byte` jest traktowany jako bez znaku.  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.10 i 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x: Array  
 Dla zapasowy CLR `x:Array` pierwotnych odpowiada <xref:System.Array>.  
  
 Można zdefiniować tablicy w języku XAML 2006 przy użyciu składni rozszerzenia znaczników; jednak składni języka XAML 2009 jest zdefiniowany w języku podstawowy, który nie wymaga dostępu do rozszerzenia znacznika. Aby uzyskać więcej informacji na temat obsługi XAML 2006, zobacz [x: Array — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Dla definicji specyfikacji języka XAML, zobacz [ \[MS XAML\] sekcje 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Obsługa WPF  
 W WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, który nie jest kompilowany do znaczników. Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.  
  
 Scenariusz, w których można użyć XAML 2009 — funkcje wraz z WPF jest Jeśli autora utracić XAML, a następnie załadować tego XAML w WPF wykres środowiska uruchomieniowego i obiektu o <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> i jego <xref:System.Windows.Markup.XamlReader.Load%2A> może przetwarzać słów kluczowych języka XAML 2009 i funkcje w reprezentację Graf prawidłowego obiektu.
