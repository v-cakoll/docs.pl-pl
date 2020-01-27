---
title: Powiązywanie kontroli z obiektem fabryki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745094"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Porady: powiązanie formantu formularzy systemu Windows z obiektem fabryki
Podczas kompilowania formantów, które współpracują z danymi, czasami trzeba będzie powiązać formant z obiektem lub metodą, która generuje inne obiekty. Taki obiekt lub metoda nazywa się fabryką. Źródło danych może być na przykład wartością zwracaną z wywołania metody zamiast obiektu w pamięci lub typu. Można powiązać kontrolkę z tym rodzajem źródła danych, o ile Źródło zwraca kolekcję.  
  
 Można łatwo powiązać formant z obiektem fabryki przy użyciu kontrolki <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób powiązania formantu <xref:System.Windows.Forms.DataGridView> z metodą fabryki przy użyciu kontrolki <xref:System.Windows.Forms.BindingSource>. Metoda Factory ma nazwę `GetOrdersByCustomerId`i zwraca wszystkie zamówienia dla danego klienta w bazie danych Northwind.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: powiązanie kontrolki Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
