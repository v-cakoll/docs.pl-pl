---
title: "Porady: powiązywanie danych z formantem DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a3c7422bc83c7ee1f09bac05333799708cd2f2f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: powiązywanie danych z formantem DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Projektant umożliwia łączenie <xref:System.Windows.Forms.DataGridView> formantu źródła danych na kilka różnych odmian, w tym baz danych, obiektów biznesowych lub usług sieci Web. Po powiązaniu formantu ze źródłem danych przy użyciu narzędzia Projektant, automatycznie formantem do <xref:System.Windows.Forms.BindingSource> składników, które reprezentuje źródło danych. Ponadto kolumny są automatycznie generowane w formancie do dopasowania informacji o schemacie udostępniane przez źródło danych.  
  
 Po kolumn, można zmodyfikować je zgodnie z potrzebami. Na przykład, usuwanie lub ukrywanie kolumn nie jest konieczne wyświetlenie, możesz zmienić kolejność kolumn lub zmodyfikować typy kolumn. Aby uzyskać więcej informacji na temat modyfikowania kolumn zobacz tematy wymienione w sekcji Zobacz też.  
  
 Może także powiązać wiele <xref:System.Windows.Forms.DataGridView> formantów w tabelach pokrewnych w celu utworzenia relacji wzorzec/szczegół. W tej konfiguracji jeden formant Wyświetla tabeli nadrzędnej i inny formant wyświetla tylko te wiersze z tabeli podrzędnej, które są powiązane z bieżącego wiersza w tabeli nadrzędnej. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie powiązanych danych w aplikacji formularzy systemu Windows](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projektu z formularza, który zawiera <xref:System.Windows.Forms.DataGridView> dwóch formantów dla relacji wzorzec/szczegół. Informacje dotyczące uruchamiania takiego projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Aby powiązać formant ze źródłem danych  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> formantu.  
  
2.  Kliknij strzałkę listy rozwijanej dla **wybierz źródło danych** opcji.  
  
3.  Jeśli projekt nie ma źródła danych, kliknij przycisk **Dodaj źródło danych projektu** i wykonaj kroki wskazane przez kreatora.  
  
     Aby uzyskać więcej informacji, zobacz [Kreator konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Nowego źródła danych będą wyświetlane w **wybierz źródło danych** okno listy rozwijanej. Jeśli nowe źródło danych zawiera tylko jeden element członkowski, takich jak tabelę pojedynczej bazy danych formant będzie automatycznie wiązane z tego członka. W przeciwnym razie przejdź do kolejnego etapu.  
  
4.  Rozwiń węzeł **inne źródła danych** i **źródła danych projektu** węzłów, jeśli nie są już rozwinięty, a następnie wybierz źródła danych, aby powiązać formant.  
  
5.  Jeśli źródło danych zawiera więcej niż jeden element członkowski, np. Jeśli utworzono <xref:System.Data.DataSet?displayProperty=nameWithType> zawiera wiele tabel, rozwiń węzeł źródła danych, a następnie wybierz określonego elementu członkowskiego do powiązania.  
  
6.  Do utworzenia relacji wzorzec/szczegół w **wybierz źródło danych** okno listy rozwijanej sekundy <xref:System.Windows.Forms.DataGridView> kontrolować, rozwiń węzeł <xref:System.Windows.Forms.BindingSource> utworzyć dla tabeli nadrzędnej, a następnie wybierz tabeli podrzędnej powiązane z listy wyświetlane.  
  
    > [!NOTE]
    >  Jeśli projekt zawiera już źródło danych, można również użyć **źródeł danych** okna, aby utworzyć dane formularza. Aby uzyskać więcej informacji, zobacz [Data Sources — okno](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [Porady: łączenie z danymi w bazie danych](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: zmienianie typu kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: ukrywanie kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: określanie kolumn jako tylko do odczytu w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Okno źródła danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [Porady: wyświetlanie powiązanych danych w systemie Windows formularzy aplikacji](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
