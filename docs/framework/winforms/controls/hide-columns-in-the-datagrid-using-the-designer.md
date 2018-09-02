---
title: 'Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 0187d85a639fc446f207a7b532fecc5ee707ae55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401647"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Czasami warto wyświetlić tylko niektóre kolumny, które są dostępne w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontroli. Na przykład możesz chcieć wyświetlić pracownika wynagrodzenia kolumny do użytkowników przy użyciu poświadczeń zarządzania podczas ukrywając je od innych użytkowników. Alternatywnie można powiązać formant ze źródłem danych, który zawiera wiele kolumn, tylko niektóre z nich, którą chcesz wyświetlić. W tym przypadku zazwyczaj spowoduje usunięcie kolumn, których nie jesteś zainteresowany wyświetlania, a nie ich. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie kolumn w Windows Forms DataGridView kontroli przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-hide-a-column-using-the-designer"></a>Aby ukryć kolumnę przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumnę z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> właściwość `false`.  
  
    > [!NOTE]
    >  Można także ukryć kolumny, podczas dodawania go, czyszcząc **Visible** pole wyboru w **Dodaj kolumnę** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Porady: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
