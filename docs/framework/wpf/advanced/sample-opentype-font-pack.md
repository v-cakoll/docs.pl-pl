---
title: Przykład pakietu czcionek OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: bec890f7937965c314ccf16b4142905c52ceff49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sample-opentype-font-pack"></a>Przykład pakietu czcionek OpenType
Ten temat zawiera omówienie przykładowej [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które są dystrybuowane wraz z [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]. Obsługa czcionek próbki rozszerzony [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcje, które mogą być używane przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Czcionki w pakiecie czcionek OpenType  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Zawiera zestaw próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki używane podczas tworzenia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Czcionki próbki są dostarczane w ramach licencji Wydłużenie górne Corporation. Tylko podzbiór całkowitej funkcje zdefiniowane przez wdrożenie tych czcionek [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format. W poniższej tabeli wymieniono nazwy próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki.  
  
|**Nazwa**|**Plik**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Perykles|Peric.ttf|  
|Jasny Perykles|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 Na poniższej ilustracji przedstawiono przykładu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] wyglądać czcionki.  
  
 ![Lista nazw czcionek w przykładowym pakiecie czcionek](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
Czcionki w pakiecie czcionek OpenType  
  
 Czcionki próbki są dostarczane w ramach licencji Wydłużenie górne Corporation. Wydłużenie górne jest dostawcą produktów zaawansowane czcionki. Aby licencji czcionki próbki w wersji rozszerzonej lub niestandardowych, zobacz [witryny sieci Web Corporation Wydłużenie górne](http://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  Projektant jest obowiązek upewnij się, że masz wymagane prawa dla żadnej czcionki osadzić w aplikacji lub w przeciwnym razie ponownie rozesłać.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalowanie czcionek  
 Istnieje możliwość zainstalowania przykładowej [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki domyślne [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] katalogu czcionki **\WINDOWS\Fonts**. Należy zainstalować czcionek czcionki w Panelu sterowania. Po te czcionki na komputerze, są dostępne dla wszystkich aplikacji, które odwołują się do domyślnego [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] czcionki. Reprezentatywny zestaw znaków w kilku rozmiary czcionek można wyświetlić, klikając podwojenie — plik czcionki. Poniższy zrzut ekranu przedstawia plik czcionki Lindsey Linds.ttf.  
  
 ![Czcionka Lindsey &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Wyświetlanie czcionki Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Używanie czcionek  
 Istnieją dwa sposoby, w której można czcionek w aplikacji. Czcionki można dodać do aplikacji projektu elementy zawartości, które nie są osadzone jako zasoby w zestawie. Alternatywnie można dodać czcionek w aplikacji jako elementy zasobów projektu, które są osadzone w aplikacji zestawu plików. Aby uzyskać więcej informacji, zobacz [czcionki tworzenia pakietów z aplikacjami](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.Typography>  
 [Funkcje czcionki OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Pakowanie czcionek z aplikacjami](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
