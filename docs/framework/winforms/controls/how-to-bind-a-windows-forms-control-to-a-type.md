---
title: Powiązywanie kontroli z typem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744985"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Porady: powiązanie formantu formularzy systemu Windows z typem
Podczas kompilowania formantów, które współpracują z danymi, czasami trzeba będzie powiązać formant z typem, a nie obiektem. Ta sytuacja występuje szczególnie w czasie projektowania, gdy dane mogą nie być dostępne, ale kontrolki powiązane z danymi nadal muszą wyświetlać informacje z interfejsu publicznego typu. Na przykład można powiązać formant <xref:System.Windows.Forms.DataGridView> z obiektem uwidocznionym przez usługę sieci Web i chcieć, aby kontrolka <xref:System.Windows.Forms.DataGridView> mogła oznaczyć kolumny w czasie projektowania z nazwami elementów członkowskich typu niestandardowego.  
  
 Można łatwo powiązać kontrolkę z typem ze składnikiem <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak powiązać formant <xref:System.Windows.Forms.DataGridView> z typem niestandardowym za pomocą składnika <xref:System.Windows.Forms.BindingSource>. Po uruchomieniu przykładu można zauważyć, że <xref:System.Windows.Forms.DataGridView> ma etykiety kolumn, które odzwierciedlają właściwości obiektu `Customer`, przed zapełnieniem formantu danymi. Przykład zawiera przycisk Dodaj klienta, aby dodać dane do kontrolki <xref:System.Windows.Forms.DataGridView>. Po kliknięciu przycisku do <xref:System.Windows.Forms.BindingSource>zostanie dodany nowy obiekt `Customer`. W rzeczywistym scenariuszu dane mogą zostać uzyskane przez wywołanie usługi sieci Web lub innego źródła danych.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
