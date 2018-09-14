---
title: 'Porady: Tworzenie formularza wzorzec / szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: 328970c5cc14669770793070942dd32f0144c159
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616673"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataGridView formularzy systemu Windows
Poniższy przykład kodu tworzy formularza wzorzec/szczegół za pomocą dwóch <xref:System.Windows.Forms.DataGridView> formanty powiązane z dwoma <xref:System.Windows.Forms.BindingSource> składników. Źródło danych jest <xref:System.Data.DataSet> zawierający `Customers` i `Orders` tabel z przykładowej bazy danych Northwind programu SQL Server wraz z <xref:System.Data.DataRelation> odnoszącej się dwa za pośrednictwem `CustomerID` kolumny.  
  
 Jeden <xref:System.Windows.Forms.BindingSource> jest powiązany z nadrzędnego `Customers` tabeli w zestawie danych. Te dane jest wyświetlany w bazie danych master <xref:System.Windows.Forms.DataGridView> kontroli. Druga <xref:System.Windows.Forms.BindingSource> jest powiązany z pierwszego łącznika danych. <xref:System.Windows.Forms.BindingSource.DataMember%2A> Właściwość drugiej <xref:System.Windows.Forms.BindingSource> ustawiono <xref:System.Data.DataRelation> nazwy. Powoduje to, że skojarzonych szczegółowych <xref:System.Windows.Forms.DataGridView> formantu, aby wyświetlić wiersze podrzędne `Orders` tabeli, które odnoszą się do bieżącego wiersza w bazie danych master <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [wskazówki: tworzenie wzorzec/szczegół formularza przy użyciu dwóch Windows formantów DataGridView formularzy](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
 Odwołania do zestawów systemu, dane systemowe, przestrzeń nazw System.Windows.Forms i System.XML.  
  
-   Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Przewodnik: tworzenie formularza wzorzec/szczegół za pomocą dwóch kontrolek DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)
