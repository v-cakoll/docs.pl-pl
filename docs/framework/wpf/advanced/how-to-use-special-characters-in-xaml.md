---
title: Jak użyć znaku specjalnego w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740842"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Jak użyć znaku specjalnego w XAML
Pliki znaczników, które są tworzone w programie Visual Studio, są automatycznie zapisywane w formacie Unicode UTF-8, co oznacza, że większość znaków specjalnych, takich jak znaki akcentu, jest poprawnie zakodowana. Jednak istnieje zestaw często używanych znaków specjalnych, które są obsługiwane inaczej. Te znaki specjalne są zgodne ze standardem XML organizacja World Wide Web Consortium (W3C) do kodowania.  
  
 W poniższej tabeli przedstawiono składnię kodowania tego zestawu znaków specjalnych:  
  
|Znak|Składnia|Opis|  
|---------------|------------|-----------------|  
|<|`&lt;`|Mniejsze niż symbol.|  
|>|`&gt;`|Znak większości.|  
|&|`&amp;`|Symbol handlowego "i".|  
|"|`&quot;`|Symbol podwójnego cudzysłowu.|  
  
> [!NOTE]
> Jeśli tworzysz plik znaczników przy użyciu edytora tekstu, takiego jak Notatnik systemu Windows, musisz zapisać plik w formacie Unicode UTF-8 pliku, aby zachować wszelkie kodowane znaki specjalne.  
  
 Poniższy przykład pokazuje, jak używać znaków specjalnych w tekście podczas tworzenia znaczników.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
