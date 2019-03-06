---
title: 'Instrukcje: Użyj zasobów w zlokalizowanych aplikacjach'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376168"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Instrukcje: Użyj zasobów w zlokalizowanych aplikacjach
Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do różnych kultur. Aby to zrobić, tekstu, takie jak tytuły, napisy, elementów pola listy i tak dalej mieć ma zostać poddany translacji. Aby ułatwić tłumaczenia elementów, które ma zostać poddany translacji są zbierane w plików zasobów. Zobacz [Lokalizuj aplikację](how-to-localize-an-application.md) informacji na temat tworzenia pliku zasobów dla lokalizacji. Zapewnienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji możliwych do zlokalizowania, umożliwiające tworzenie lokalizowalne zasoby w ramach zestawu zasobów. Zestaw zasobów jest zlokalizowany w różnych językach i korzysta z kodem — zarządzanie zasobami [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do załadowania. Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji to plik projektu (plików Proj). Wszystkie zasoby, których używasz w aplikacji powinny być objęte w pliku projektu. Poniższy przykład kodu pokazuje to.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Aby korzystać z zasobów w aplikacji, wystąpienia <xref:System.Resources.ResourceManager> i załaduj zasób, którego chcesz użyć. Poniżej pokazano, jak to zrobić.  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
