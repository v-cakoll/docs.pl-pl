---
title: Sprawdzanie poprawności danych w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728309"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Porady: sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows
Poniższy przykład kodu demonstruje, jak sprawdzać poprawność danych wprowadzonych przez użytkownika w kontrolce <xref:System.Windows.Forms.DataGridView>. W tym przykładzie <xref:System.Windows.Forms.DataGridView> jest wypełniany wierszami z tabeli `Customers` przykładowej bazy danych Northwind. Gdy użytkownik edytuje komórkę w `CompanyName` kolumnie, jej wartość jest testowana pod kątem ważności, sprawdzając, czy nie jest pusta. Jeśli program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValidating> stwierdzi, że wartość jest pustym ciągiem, <xref:System.Windows.Forms.DataGridView> uniemożliwia użytkownikowi opuszczenie komórki do momentu wprowadzenia niepustego ciągu.  
  
 Aby uzyskać kompletny opis tego przykładu kodu, zobacz [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Windows. Forms i system. XML.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
