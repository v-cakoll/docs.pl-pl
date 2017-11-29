---
title: "Porady: powiązanie formantów formularzy systemu Windows z wartościami bazy danych DBNull"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2917288a92426c6afe9f4f97cca353c74dc954e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Porady: powiązanie formantów formularzy systemu Windows z wartościami bazy danych DBNull
Po powiązaniu formanty formularzy systemu Windows do źródła danych i źródle danych zwraca <xref:System.DBNull> wartość odpowiednią wartość można zastąpić bez obsługi, formatowanie i analizowanie zdarzeń. <xref:System.Windows.Forms.Binding.NullValue%2A> Przekonwertuje właściwości <xref:System.DBNull> określony obiekt podczas formatowania lub analizowania wartości źródła danych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak można powiązać <xref:System.DBNull> wartość w dwóch różnych sytuacjach. Pierwszy pokazano, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości ciągu; druga pokazano, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości obrazu.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Typy właściwości powiązania i <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości musi być taka sama lub spowoduje błąd i nie musisz <xref:System.Windows.Forms.Binding.NullValue%2A> wartości zostaną przetworzone. W takiej sytuacji zostanie nie wyjątek.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [Porady: powiązanie formantu formularzy systemu Windows z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
