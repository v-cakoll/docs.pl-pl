---
title: 'Instrukcje: Używanie zasobów w lokalizowalnych aplikacjach'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 3634bb72cbacfb02b0a1230a47a1664cb8ce5009
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238459"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>Instrukcje: Używanie zasobów w lokalizowalnych aplikacjach
Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do różnych kultur. Aby to zrobić, tekstu, takie jak tytuły, napisy, elementów pola listy i tak dalej mieć ma zostać poddany translacji. Aby ułatwić tłumaczenia elementów, które ma zostać poddany translacji są zbierane w plików zasobów. Zobacz [Lokalizuj aplikację](how-to-localize-an-application.md) informacji na temat tworzenia pliku zasobów dla lokalizacji. Zapewnienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji możliwych do zlokalizowania, umożliwiające tworzenie lokalizowalne zasoby w ramach zestawu zasobów. Zestaw zasobów jest zlokalizowany w różnych językach i związane z kodem wykorzystuje interfejs API zarządzania zasobami można załadować. Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji to plik projektu (plików Proj). Wszystkie zasoby, których używasz w aplikacji powinny być objęte w pliku projektu. Poniższy przykład kodu pokazuje to.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Aby korzystać z zasobów w aplikacji, wystąpienia <xref:System.Resources.ResourceManager> i załaduj zasób, którego chcesz użyć. Poniżej pokazano, jak to zrobić.  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
