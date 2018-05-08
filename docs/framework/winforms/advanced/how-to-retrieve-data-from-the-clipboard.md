---
title: 'Porady: pobieranie danych ze schowka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: e06fb509bed32df0c18f2a03ae89765b3334b2c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Porady: pobieranie danych ze schowka
<xref:System.Windows.Forms.Clipboard> Klasa dostarcza metody, które służy do interakcji z funkcją Schowka systemu operacyjnego Windows. Wiele aplikacji korzysta Schowka jako tymczasowy repozytorium dla danych. Na przykład edytory użyć Schowka podczas operacji kopiowania i wklejania. Schowek jest również przydatne w przypadku przenoszenia informacji z jednej aplikacji do innej.  
  
 Niektóre aplikacje przechowują dane do Schowka w wielu formatach, aby zwiększyć liczbę inne aplikacje, które mogą za pomocą danych. Format Schowka jest ciągiem, który identyfikuje format. Aplikacja, która używa formatu zidentyfikowanych można pobrać skojarzone dane do Schowka. <xref:System.Windows.Forms.DataFormats> Klasy udostępnia wstępnie zdefiniowane format nazwy do użycia. Możesz również użyć nazwy formatu lub typ obiektu jako jego format. Aby uzyskać informacje dotyczące dodawania danych do Schowka, zobacz [porady: Dodawanie danych do Schowka](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Aby ustalić, czy Schowek zawiera dane w określonym formacie, użyj jednej z `Contains` *Format* metody lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Aby pobrać danych ze Schowka, użyj jednej z `Get` *Format* metody lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Te metody są nowością w programie [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Dostęp do danych ze Schowka za pomocą wersji starszej niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], użyj <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> — metoda i wywoływać metod zwróconego elementu <xref:System.Windows.Forms.IDataObject>. Aby sprawdzić, czy określony format jest dostępna w zwrócony obiekt, na przykład wywołać <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metody.  
  
> [!NOTE]
>  Wszystkie aplikacje systemu Windows Udostępnianie Schowka systemu Windows. W związku z tym zawartość mogą ulec zmianie po przełączeniu do innej aplikacji.  
>   
>  <xref:System.Windows.Forms.Clipboard> Klasy można używać tylko w wątkach ustawiony na tryb Jednowątkowego apartamentu wątku pojedynczego. Aby korzystać z tej klasy, upewnij się, że Twoje `Main` metoda jest oznaczona atrybutem <xref:System.STAThreadAttribute> atrybutu.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Można pobrać danych ze Schowka w formacie jednej, wspólnej  
  
1.  Użyj <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, lub <xref:System.Windows.Forms.Clipboard.GetText%2A> metody. Można też użyć odpowiedniego `Contains` *Format* metod, aby ustalić, czy dane są dostępne w określonym formacie. Te metody są dostępne tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Można pobrać danych ze Schowka w niestandardowym formacie  
  
1.  Użyj <xref:System.Windows.Forms.Clipboard.GetData%2A> metodę o nazwie formatu niestandardowego. Ta metoda jest dostępna tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Można również użyć nazwy formatu wstępnie zdefiniowane z <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Można pobrać danych ze Schowka w wielu formatach  
  
1.  Użyj <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metody. Tej metody należy użyć do pobierania danych ze Schowka w wersjach wcześniejszych niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje przeciągania i upuszczania oraz obsługa schowka](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Instrukcje: dodawanie danych do schowka](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
