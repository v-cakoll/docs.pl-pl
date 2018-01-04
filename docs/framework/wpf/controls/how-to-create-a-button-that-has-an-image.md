---
title: "Jak utworzyć przycisk, który posiada obraz"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e95f027a8e3568365fa7957c36241b6ec2c30d28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Jak utworzyć przycisk, który posiada obraz
W tym przykładzie pokazano, jak dołączyć obrazu na <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Button> kontrolki. Jeden <xref:System.Windows.Controls.Button> zawiera tekst, a drugi zawiera obraz. Obraz znajduje się w folderze o nazwie danych, który jest podfolderem folderu projektu w przykładzie. Gdy użytkownik kliknie <xref:System.Windows.Controls.Button> mający obrazu, tła i tekstu z innych <xref:System.Windows.Controls.Button> zmienić.  
  
 Ten przykład tworzy <xref:System.Windows.Controls.Button> steruje się za pomocą znacznika, ale kod używany do zapisu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedury obsługi zdarzeń.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki](../../../../docs/framework/wpf/controls/index.md)  
 [Biblioteka kontrolek](../../../../docs/framework/wpf/controls/control-library.md)
