---
title: 'Porady: powiązanie formantu formularzy systemu Windows z typem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 1130eba7b92ecb5adeba2df9601a31637823754e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530097"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Porady: powiązanie formantu formularzy systemu Windows z typem
Podczas tworzenia formantów, które współdziałają z danymi będą czasami jest konieczne do wiązania kontrolki typu, a nie obiektu. Taka sytuacja wystąpi szczególnie w czasie projektowania, gdy dane mogą nie być dostępne, ale formantów powiązanych z danymi nadal konieczne jest wyświetlenie informacji dotyczących interfejsu publicznego typu. Na przykład może powiązać <xref:System.Windows.Forms.DataGridView> kontrolować obiektem udostępnianych przez usługi sieci Web i chcesz <xref:System.Windows.Forms.DataGridView> formantu etykiety kolumn w czasie projektowania z elementem członkowskim nazwy typu niestandardowego.  
  
 Łatwo można powiązać formant do typu z <xref:System.Windows.Forms.BindingSource> składnika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak można powiązać <xref:System.Windows.Forms.DataGridView> formantu niestandardowego typu przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. Po uruchomieniu przykładzie można zauważyć <xref:System.Windows.Forms.DataGridView> etykietą kolumny, które odzwierciedlać właściwości `Customer` obiektu, zanim formant został wypełniony danymi. Przykład znajduje się przycisk Dodaj klienta do dodawania danych do <xref:System.Windows.Forms.DataGridView> formantu. Po kliknięciu przycisku Nowy `Customer` obiekt jest dodawany do <xref:System.Windows.Forms.BindingSource>. W przypadku rzeczywistych danych może można uzyskać przez wywołanie do usługi sieci Web lub innego źródła danych.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
