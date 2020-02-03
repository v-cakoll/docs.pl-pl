---
title: Tworzenie formularza z szczegółami głównymi przy użyciu dwóch formantów DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737333"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows
Poniższy przykład kodu tworzy formularz wzorzec/szczegół za pomocą dwóch formantów <xref:System.Windows.Forms.DataGridView> powiązanych z dwoma składnikami <xref:System.Windows.Forms.BindingSource>. Źródło danych to <xref:System.Data.DataSet>, które zawiera tabele `Customers` i `Orders` z przykładowej bazy danych Northwind SQL Server wraz z <xref:System.Data.DataRelation>, który wiąże te dwa za pośrednictwem kolumny `CustomerID`.  
  
 Jeden <xref:System.Windows.Forms.BindingSource> jest powiązany z tabelą nadrzędną `Customers` w zestawie danych. Te dane są wyświetlane w głównym formancie <xref:System.Windows.Forms.DataGridView>. Inne <xref:System.Windows.Forms.BindingSource> są powiązane z pierwszym łącznikiem danych. Właściwość <xref:System.Windows.Forms.BindingSource.DataMember%2A> drugiego <xref:System.Windows.Forms.BindingSource> jest ustawiona na nazwę <xref:System.Data.DataRelation>. Powoduje to, że skojarzona szczegółowo formant <xref:System.Windows.Forms.DataGridView> formantu, aby wyświetlić wiersze podrzędnej tabeli `Orders`, która odpowiada bieżącemu wierszowi w głównym formancie <xref:System.Windows.Forms.DataGridView>.  
  
 Aby uzyskać kompletny opis tego przykładu kodu, zobacz [Przewodnik: Tworzenie formularza wzorzec/szczegół za pomocą dwóch Windows Forms formantów DataGridView](creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
 Odwołania do zestawów system, system. Data, system. Windows. Forms i system. XML.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](creating-a-master-detail-form-using-two-datagridviews.md)
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
