---
title: 'Instrukcje: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952692"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Instrukcje: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows
Podczas kompilowania aplikacji opartych na danych często konieczne jest wyświetlenie kolekcji danych dla użytkowników. Kontrolka, w połączeniu <xref:System.Windows.Forms.BindingSource> z składnikiem, oferuje wygodne i rozszerzalne rozwiązanie do poruszania się po kolekcji i wyświetlania elementów sekwencyjnie. <xref:System.Windows.Forms.BindingNavigator>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak używać <xref:System.Windows.Forms.BindingNavigator> kontrolki do przenoszenia danych. Zestaw jest zawarty w <xref:System.Data.DataView>, który jest powiązany <xref:System.Windows.Forms.TextBox> z kontrolką ze <xref:System.Windows.Forms.BindingSource> składnikiem.  
  
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
- [Instrukcje: Powiąż formant Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
