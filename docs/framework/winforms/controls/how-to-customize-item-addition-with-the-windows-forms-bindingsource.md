---
title: 'Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 299b24eb42c576535389f53982581bf4a776ee3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531030"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows
Jeśli używasz <xref:System.Windows.Forms.BindingSource> składnika powiązanie formantu formularzy systemu Windows ze źródłem danych może być konieczne dostosowanie tworzenie nowych elementów. <xref:System.Windows.Forms.BindingSource> Składnika sprawia, że to proste zapewniając <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, które zwykle jest wywoływane, gdy formant związany potrzebuje do utworzenia nowego elementu. Obsługi zdarzenia zapewniają wszelkie niestandardowe zachowanie jest wymagana (na przykład wywołanie metody usługi sieci Web lub wprowadzenie nowego obiektu z fabryki klasy).  
  
> [!NOTE]
>  Po dodaniu elementu Obsługa <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzeń, nie można anulować operacji dodawania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Forms.DataGridView> formantu fabrykę klas przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. Po kliknięciu przez użytkownika <xref:System.Windows.Forms.DataGridView> formantu nowy wiersz <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenia. Tworzy nową klasę programu obsługi zdarzeń `DemoCustomer` obiektu, który jest przypisany do <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> właściwości. Powoduje to, że nowe `DemoCustomer` obiekt ma zostać dodany do <xref:System.Windows.Forms.BindingSource> listy składnika i mają być wyświetlane w nowym wierszu <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Instrukcje: powiązanie kontrolki Windows Forms z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
