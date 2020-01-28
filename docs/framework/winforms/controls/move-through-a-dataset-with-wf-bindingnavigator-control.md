---
title: Przechodzenie przez zestaw danych przy użyciu kontrolki BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742151"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Porady: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows
Podczas kompilowania aplikacji opartych na danych często konieczne jest wyświetlenie kolekcji danych dla użytkowników. Kontrolka <xref:System.Windows.Forms.BindingNavigator>, w połączeniu ze składnikiem <xref:System.Windows.Forms.BindingSource>, oferuje wygodne i rozszerzalne rozwiązanie do poruszania się po kolekcji i wyświetlania elementów sekwencyjnie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje sposób używania kontrolki <xref:System.Windows.Forms.BindingNavigator> do przenoszenia danych. Zestaw jest zawarty w <xref:System.Data.DataView>, który jest powiązany z kontrolką <xref:System.Windows.Forms.TextBox> ze składnikiem <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
> Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing, system. Windows. Forms i system. XML.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: powiązanie kontrolki Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
