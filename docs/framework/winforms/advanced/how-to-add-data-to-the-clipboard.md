---
title: 'Porady: dodawanie danych do schowka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 6002acfadfd0e688ef432baacbdabffb83890cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-data-to-the-clipboard"></a>Porady: dodawanie danych do schowka
<xref:System.Windows.Forms.Clipboard> Klasa dostarcza metody, które służy do interakcji z funkcją Schowka systemu operacyjnego Windows. Wiele aplikacji korzysta Schowka jako tymczasowy repozytorium dla danych. Na przykład edytory użyć Schowka podczas operacji kopiowania i wklejania. Schowek jest również przydatne w przypadku transferu danych między aplikacjami na inny.  
  
 Podczas dodawania danych do Schowka, można określić format danych tak, aby inne aplikacje mogą rozpoznaje danych, jeśli będzie mógł używać tego formatu. Można również dodać dane do Schowka w wielu różnych formatach, aby zwiększyć liczbę inne aplikacje, które mogą za pomocą danych.  
  
 Format Schowka jest ciągiem, który określa format, dzięki czemu aplikacji korzystającej z tego formatu można pobrać skojarzonych danych. <xref:System.Windows.Forms.DataFormats> Klasy udostępnia wstępnie zdefiniowane format nazwy do użycia. Możesz również użyć nazwy formatu lub typ obiektu jako jego format.  
  
 Aby dodać dane do Schowka w jednej lub wielu formatów, należy użyć <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metody. Dowolny obiekt można przekazać do tej metody, ale można dodać danych w wielu formatach, należy najpierw dodać dane do oddzielny obiekt przeznaczony do pracy w wielu formatach. Zazwyczaj spowoduje dodanie danych do <xref:System.Windows.Forms.DataObject>, ale można użyć dowolnego typu, który implementuje <xref:System.Windows.Forms.IDataObject> interfejsu.  
  
 W [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], dane bezpośrednio do Schowka można dodać przy użyciu nowych metod, które umożliwiają wykonywanie podstawowych zadań Schowka. Podczas pracy z danymi w formacie jednej, wspólnej, taki jak tekst za pomocą tych metod.  
  
> [!NOTE]
>  Wszystkie aplikacje systemu Windows Udostępnianie Schowka. W związku z tym zawartość mogą ulec zmianie po przełączeniu do innej aplikacji.  
>   
>  <xref:System.Windows.Forms.Clipboard> Klasy można używać tylko w wątkach ustawiony na tryb Jednowątkowego apartamentu wątku pojedynczego. Aby korzystać z tej klasy, upewnij się, że Twoje `Main` metoda jest oznaczona atrybutem <xref:System.STAThreadAttribute> atrybutu.  
>   
>  Obiekt musi być możliwy do serializacji dla niego do umieszczenia w Schowku. Aby typ możliwy do serializacji, oznacz go z <xref:System.SerializableAttribute> atrybutu. Nie można serializować obiektu są przekazywane do metody Schowka, metoda zakończy się niepowodzeniem bez generowania wyjątku. Aby uzyskać więcej informacji na temat serializacji, zobacz <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Aby dodać dane do Schowka w formacie jednej, wspólnej  
  
1.  Użyj <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, lub <xref:System.Windows.Forms.Clipboard.SetText%2A> metody. Te metody są dostępne tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Aby dodać dane do Schowka w niestandardowym formacie  
  
1.  Użyj <xref:System.Windows.Forms.Clipboard.SetData%2A> metodę o nazwie formatu niestandardowego. Ta metoda jest dostępna tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Można również użyć nazwy formatu wstępnie zdefiniowane z <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Aby dodać dane do Schowka w wielu formatach  
  
1.  Użyj <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> — metoda i przekaż <xref:System.Windows.Forms.DataObject> zawierający dane. Tej metody należy użyć, aby dodać dane do Schowka w wersjach wcześniejszych niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje przeciągania i upuszczania oraz obsługa schowka](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Instrukcje: pobieranie danych ze schowka](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
