---
title: Przykład pakietu czcionek OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 30cb69fcf05108822e8f3e2d45c9e79dbced26ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181911"
---
# <a name="sample-opentype-font-pack"></a>Przykład pakietu czcionek OpenType
Ten temat zawiera omówienie przykładowych czcionek OpenType, które są dystrybuowane z zestawem Windows SDK. Przykładowe czcionki obsługują rozszerzone funkcje OpenType, które mogą być używane przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacje.  

<a name="overview"></a>
## <a name="fonts-in-the-opentype-font-pack"></a>Czcionki w pakiecie czcionek OpenType  
 Zestaw Windows SDK zawiera zestaw przykładowych czcionek OpenType, których można używać podczas tworzenia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Przykładowe czcionki są dostarczane na licencji firmy Ascender Corporation. Czcionki te implementują tylko podzbiór całkowitych funkcji zdefiniowanych przez format OpenType. W poniższej tabeli wymieniono nazwy przykładowych czcionek OpenType.  
  
|**Nazwa**|**Plik**|  
|--------------|--------------|  
|Okręg wyborczy Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Perykles|Peric.ttf|  
|Światło peryklesowe|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Pogrubienie|Pescab.ttf|  
  
 Na poniższej ilustracji przedstawiono, jak wyglądają przykładowe czcionki OpenType.  
  
 ![Lista nazw czcionek w przykładowym pakiecie czcionek](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Przykładowe czcionki są dostarczane na licencji firmy Ascender Corporation. Ascender jest dostawcą zaawansowanych produktów czcionek. Aby uzyskać licencję na rozszerzone lub niestandardowe wersje przykładowych czcionek, zobacz [witrynę firmy Ascender Corporation w sieci Web](https://www.monotype.com/).  
  
> [!NOTE]
> Jako programista użytkownik jest odpowiedzialny za zapewnienie wymaganych praw licencyjnych dla dowolnej czcionki, którą osadzasz w aplikacji lub w inny sposób redystrybuujesz.  
  
<a name="installing_the_fonts"></a>
## <a name="installing-the-fonts"></a>Instalowanie czcionek  
 Można zainstalować przykładowe czcionki OpenType w domyślnym katalogu Czcionek systemu Windows **\WINDOWS\Fonts**. Użyj panelu sterowania Czcionki, aby zainstalować czcionki. Gdy te czcionki znajdują się na komputerze, są dostępne dla wszystkich aplikacji, które odwołują się do domyślnych czcionek systemu Windows. Można wyświetlić reprezentatywny zestaw znaków w kilku rozmiarach czcionek, podwajając klikanie pliku czcionki. Poniższy zrzut ekranu przedstawia plik czcionki Lindsey, Linds.ttf.  
  
 ![Czcionka Lindsey &#40;&#41;OpenType](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Wyświetlanie czcionki Lindsey  
  
<a name="using_the_fonts"></a>
## <a name="using-the-fonts"></a>Korzystanie z czcionek  
 Istnieją dwa sposoby używania czcionek w aplikacji. Czcionki można dodawać do aplikacji jako elementy zawartości projektu, które nie są osadzone jako zasoby w zestawie. Alternatywnie można dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w plikach zestawu aplikacji. Aby uzyskać więcej informacji, zobacz [Pakowanie czcionek za pomocą aplikacji](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Documents.Typography>
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Pakowanie czcionek z aplikacjami](packaging-fonts-with-applications.md)
