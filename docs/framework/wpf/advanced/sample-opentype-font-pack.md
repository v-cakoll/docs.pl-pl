---
title: Przykład pakietu czcionek OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: be9bc6e0cddc0581b9acb319f7d1fc1c81dae268
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095115"
---
# <a name="sample-opentype-font-pack"></a>Przykład pakietu czcionek OpenType
Ten temat zawiera omówienie przykładowych czcionek OpenType, które są dystrybuowane z Windows SDK. Przykładowe czcionki obsługują rozszerzone funkcje OpenType, które mogą być używane przez aplikacje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Czcionki w pakiecie czcionek OpenType  
 Windows SDK zawiera zestaw przykładowych czcionek OpenType, których można użyć podczas tworzenia aplikacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Przykładowe czcionki są dostarczane w ramach licencji od firmy Ascend Corporation. Te czcionki implementują tylko podzestaw całkowitej liczby funkcji zdefiniowanych przez format OpenType. W poniższej tabeli wymieniono nazwy przykładowych czcionek OpenType.  
  
|**Nazwa**|**Plik**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Pogrubienie Miramonte|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pogrubienie Pescadero|Pescab.ttf|  
  
 Na poniższej ilustracji przedstawiono, jak wyglądają przykładowe czcionki OpenType.  
  
 ![Lista nazw czcionek w przykładowym pakiecie czcionek](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Przykładowe czcionki są dostarczane w ramach licencji od firmy Ascend Corporation. Ascender to dostawca zaawansowanych produktów czcionek. Aby uzyskać licencję na rozszerzoną lub niestandardową wersję przykładowych czcionek, zobacz [witrynę sieci Web firmy Ascender](https://www.monotype.com/).  
  
> [!NOTE]
> Deweloperem jest odpowiedzialność za upewnienie się, że masz wymagane prawa licencji dla dowolnej czcionki osadzonej w aplikacji lub w inny sposób.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalowanie czcionek  
 Możesz zainstalować przykładowe czcionki OpenType w domyślnym katalogu czcionek systemu Windows, **\Windows\Fonts**. Za pomocą panelu sterowania czcionki Zainstaluj czcionki. Gdy te czcionki znajdują się na komputerze, są dostępne dla wszystkich aplikacji, które odwołują się do domyślnych czcionek systemu Windows. Można wyświetlić reprezentatywny zestaw znaków w kilku rozmiarach czcionek, podwajając kliknięcie pliku z czcionką. Poniższy zrzut ekranu przedstawia plik z czcionką Lindsey, Linds. ttf.  
  
 ![Czcionka &#40;Lindsey OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Wyświetlanie czcionki Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Używanie czcionek  
 Istnieją dwa sposoby używania czcionek w aplikacji. Możesz dodać czcionki do aplikacji jako elementy zawartości projektu, które nie są osadzane jako zasoby w ramach zestawu. Alternatywnie możesz dodać czcionki do aplikacji jako elementy zasobów projektu, które są osadzone w plikach zestawu aplikacji. Aby uzyskać więcej informacji, zobacz [pakowanie czcionek z aplikacjami](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Documents.Typography>
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Pakowanie czcionek z aplikacjami](packaging-fonts-with-applications.md)
