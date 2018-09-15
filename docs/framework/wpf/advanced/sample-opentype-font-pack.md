---
title: Przykład pakietu czcionek OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 93bba86801ec4971e884cb4703d7a6323a2e94fe
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625831"
---
# <a name="sample-opentype-font-pack"></a>Przykład pakietu czcionek OpenType
Ten temat zawiera omówienie przykładu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które są dystrybuowane za pomocą [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]. Rozszerzono obsługę czcionki przykładowe [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcje, które mogą być używane przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Czcionki w pakietu czcionek OpenType  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Udostępnia zestaw przykładowych [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można użyć podczas tworzenia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Czcionki próbki są dostarczane w ramach licencji Wydłużenie górne Corporation. Te czcionki zaimplementować tylko podzbiór łączna liczba funkcji zdefiniowanych przez [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] formatu. W poniższej tabeli wymieniono nazwy próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki.  
  
|**Nazwa**|**Plik**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte pogrubienia|Miramob.ttf|  
|Perykles|Peric.ttf|  
|Perykles światła|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero pogrubienia|Pescab.ttf|  
  
 Na poniższej ilustracji przedstawiono przykładu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] wyglądać czcionki.  
  
 ![Listy nazw czcionki, na przykład pakietu czcionek](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
Czcionki w pakietu czcionek OpenType  
  
 Czcionki próbki są dostarczane w ramach licencji Wydłużenie górne Corporation. Wydłużenie górne to dostawca produktów zaawansowane czcionki. Licencje wersji rozszerzonej lub niestandardowych czcionek przykładowe, zobacz [witryny sieci Web Corporation Wydłużenie górne](https://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  Jako deweloper jest odpowiedzialny za zapewnienie, że masz prawa wymaganą licencję dla czcionki, które można osadzić w aplikacji lub w inny sposób.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalowanie czcionek  
 Istnieje możliwość zainstalowania próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki domyślną [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] katalog czcionek **\WINDOWS\Fonts**. Za pomocą Panelu sterowania czcionki do instalowania czcionek. Gdy te czcionki znajdują się na komputerze, są one dostępne dla wszystkich aplikacji, które odwołują się domyślne [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] czcionki. Reprezentatywny zestaw znaków w kilku rozmiary czcionek można wyświetlić, klikając podwojenie — plik czcionki. Poniższy zrzut ekranu przedstawia plik czcionki Lindsey Linds.ttf.  
  
 ![Czcionka Lindsey &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Wyświetlanie Czcionka Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Za pomocą czcionek  
 Istnieją dwa sposoby, że można używać czcionek w aplikacji. Możesz dodać czcionki do aplikacji jako elementy zawartości, które nie są osadzane jako zasoby w zestawie projektu. Alternatywnie możesz dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w ramach plików zestawu aplikacji. Aby uzyskać więcej informacji, zobacz [pakowanie czcionek z aplikacjami](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.Typography>  
 [Funkcje czcionki OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Pakowanie czcionek z aplikacjami](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
