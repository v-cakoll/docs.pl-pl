---
title: 'Instrukcje: Implementowanie interfejsu IListSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
ms.openlocfilehash: bd4e554b7e4be51847496307b50be3084d0115d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159786"
---
# <a name="how-to-implement-the-ilistsource-interface"></a>Instrukcje: Implementowanie interfejsu IListSource
Implementowanie <xref:System.ComponentModel.IListSource> interfejsu do utworzenia możliwej do wiązania klasy, który nie implementuje <xref:System.Collections.IList> , ale zamiast tego zawiera listę z innej lokalizacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.IListSource> interfejsu. Składnik o nazwie `EmployeeListSource` udostępnia <xref:System.Collections.IList> dla powiązania danych poprzez implementację <xref:System.ComponentModel.IListSource.GetList%2A> metody.  
  
 [!code-csharp[System.ComponentModel.IListSource#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.IListSource>
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [Wiązanie danych i formularze systemu Windows](data-binding-and-windows-forms.md)
