---
title: "Jak powiązać ListBox z danymi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: deb5e05a7c48f26d0b829ba75b4ae120841e0a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a>Jak powiązać ListBox z danymi
Deweloper aplikacji można utworzyć <xref:System.Windows.Controls.ListBox> formantów bez określania zawartości każdego <xref:System.Windows.Controls.ListBoxItem> oddzielnie. Powiązanie danych służy do powiązania danych do poszczególnych elementów.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.ListBox> który wypełnia <xref:System.Windows.Controls.ListBoxItem> elementów przez powiązanie danych ze źródłem danych o nazwie *kolory*. W takim przypadku nie jest konieczne użycie <xref:System.Windows.Controls.ListBoxItem> tagi umożliwia określenie zawartości każdego elementu.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [Formanty](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
