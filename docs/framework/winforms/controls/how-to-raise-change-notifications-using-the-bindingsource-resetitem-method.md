---
title: 'Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: eb97191e30cd2c4eb5ad8b8bbc158819ac1fe396
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261417"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem
Niektóre źródła danych dla kontrolki nie wywoływanie powiadomień o zmianie, gdy elementy są zmieniane, dodawane lub usuwane. Za pomocą <xref:System.Windows.Forms.BindingSource> składnik, można powiązać z takich źródeł danych i zgłosić powiadomienia o zmianach w kodzie.  
  
## <a name="example"></a>Przykład  
 Ten formularz, który demonstruje sposób użycia <xref:System.Windows.Forms.BindingSource> składnik do listy, aby powiązać <xref:System.Windows.Forms.DataGridView> kontroli. Listy nie powoduje powiadomienia o zmianie, więc <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metody <xref:System.Windows.Forms.BindingSource> jest wywoływana, gdy element na liście zostanie zmieniony. .  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [Instrukcje: Powiązanie z typem formantu Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
