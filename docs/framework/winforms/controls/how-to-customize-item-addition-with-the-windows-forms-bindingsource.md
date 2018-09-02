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
ms.openlocfilehash: f8956ceb8da2aa14aea8b7e62b9d60ab656a3891
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405218"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a>Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows
Kiedy używasz <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać formant programu Windows Forms ze źródłem danych może okazać się konieczne dostosowanie tworzenia nowych elementów. <xref:System.Windows.Forms.BindingSource> Ze składników zgłasza to prosta, zapewniając <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, które zazwyczaj jest inicjowane, gdy formant związany potrzebne do utworzenia nowego elementu. Procedury obsługi zdarzenia może zapewnić dowolne niestandardowe zachowanie jest wymagana (na przykład, wywołanie metody usługi sieci Web lub wprowadzenie nowego obiektu z fabryki klas).  
  
> [!NOTE]
>  Gdy element zostanie dodany do obsługi <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzeń, nie można anulować dodawanie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Forms.DataGridView> kontrolki fabryki klas przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. Kiedy użytkownik kliknie <xref:System.Windows.Forms.DataGridView> kontrolki nowy wiersz <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie jest wywoływane. Program obsługi zdarzeń tworzy nową `DemoCustomer` obiektu, który jest przypisany do <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> właściwości. Powoduje to, że nowe `DemoCustomer` obiektów, które mają zostać dodane do <xref:System.Windows.Forms.BindingSource> listy składnika i mają być wyświetlane w nowym wierszu <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Instrukcje: powiązanie kontrolki Windows Forms z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
