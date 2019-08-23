---
title: 'Instrukcje: Używanie znaku specjalnego w XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918437"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Instrukcje: Używanie znaku specjalnego w XAML
Pliki znaczników, które są tworzone [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] w programie, są automatycznie [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] zapisywane w formacie pliku UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana. Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej. Te znaki specjalne są zgodne [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] ze [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardem kodowania.  
  
 W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:  
  
|Znak|Składnia|Opis|  
|---------------|------------|-----------------|  
|<|`&lt;`|Mniejsze niż symbol.|  
|>|`&gt;`|Znak większości.|  
|&|`&amp;`|Symbol handlowego "i".|  
|"|`&quot;`|Symbol podwójnego cudzysłowu.|  
  
> [!NOTE]
> Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formacie UTF-8, aby zachować wszelkie zakodowane znaki specjalne.  
  
 Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
