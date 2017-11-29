---
title: "Jak użyć znaku specjalnego w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 308b2152f98286ba532a15e5491b5d1a25aa66dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a>Jak użyć znaku specjalnego w XAML
Pliki znaczników, które są tworzone w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] są automatycznie zapisywane w [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format pliku UTF-8, co oznacza, że kodowania znaków specjalnych, takich jak znaki akcentu. Istnieje jednak zestaw często używane znaki specjalne, które są obsługiwane w inny sposób. Postępuj zgodnie z tych znaków specjalnych [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standardowa do kodowania.  
  
 W poniższej tabeli przedstawiono składnię kodowanie tego zestawu znaków specjalnych:  
  
|Znak|Składnia|Opis|  
|---------------|------------|-----------------|  
|<|`<`|Mniej niż symbol.|  
|>|`>`|Większa niż znak.|  
|&|`&`|Symbol handlowego "i".|  
|"|`"`|Symbol podwójnego cudzysłowu.|  
  
> [!NOTE]
>  Jeśli utworzysz plik kodu znaczników przy użyciu tekstu edytor, takich jak [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notatnik, możesz zapisać plik [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kodowany w formacie UTF-8 w celu zachowania wszelkie znaki specjalne.  
  
 Poniższy przykład przedstawia sposób korzystania znaki specjalne w tekście podczas tworzenia znaczników.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
