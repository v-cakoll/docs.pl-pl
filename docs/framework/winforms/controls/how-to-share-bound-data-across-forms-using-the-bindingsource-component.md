---
title: 'Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956071"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource
Możesz łatwo udostępniać dane między formularzami przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. Na przykład możesz chcieć wyświetlić jeden formularz tylko do odczytu, który podsumowuje dane źródła danych i inny formularz edytowalny, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych. Ten przykład ilustruje ten scenariusz.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje <xref:System.Windows.Forms.BindingSource> , jak udostępniać dane i powiązane z nią powiązania w formularzach. W tym przykładzie udostępniony <xref:System.Windows.Forms.BindingSource> jest przesyłany do konstruktora formularza podrzędnego. Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.  
  
> [!NOTE]
> <xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenie<xref:System.Windows.Forms.BindingSource> dla składnika jest obsługiwane w przykładzie, aby upewnić się, że dwa formularze pozostają zsynchronizowane. Aby uzyskać więcej informacji na temat tego, jak to [zrobić, zobacz How to: Upewnij się, że wiele kontrolek powiązanych z tym samym](../multiple-controls-bound-to-data-source-synchronized.md)źródłem danych pozostanie zsynchronizowane.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Windows. Forms, system. Drawing, system. Data i system. XML.  
  
## <a name="see-also"></a>Zobacz także

- [BindingSource, składnik](bindingsource-component.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Instrukcje: Obsługa błędów i wyjątków występujących podczas wiązania z danymi](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
