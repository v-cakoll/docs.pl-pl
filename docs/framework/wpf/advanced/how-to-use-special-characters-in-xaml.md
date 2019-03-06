---
title: 'Instrukcje: Użyj znaku specjalnego w XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377966"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Instrukcje: Użyj znaku specjalnego w XAML
Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format pliku UTF-8, co oznacza, że znaków specjalnych, takich jak znaki akcentu są kodowane niepoprawnie. Jednak to zbiór często używane znaki specjalne, które są obsługiwane w inny sposób. Postępuj zgodnie z tych znaków specjalnych [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard kodowania.  
  
 W poniższej tabeli przedstawiono składnię tego zestawu znaków specjalnych kodowania:  
  
|Znak|Składnia|Opis|  
|---------------|------------|-----------------|  
|<|`&lt;`|Mniej niż symbol.|  
|>|`&gt;`|Większa niż logowania.|  
|&|`&amp;`|Symbol handlowego "i".|  
|"|`&quot;`|Symbol podwójnego cudzysłowu.|  
  
> [!NOTE]
>  Jeśli tworzysz pliku znaczników przy użyciu typu text editor, takich jak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notatnik, musisz zapisać plik w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodowany w formacie UTF-8 w celu zachowania dowolne znaki specjalne.  
  
 Poniższy przykład pokazuje, jak możesz mogą używać znaków specjalnych w tekście podczas tworzenia znaczników.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
