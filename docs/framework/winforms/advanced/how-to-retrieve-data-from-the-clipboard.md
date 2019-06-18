---
title: 'Instrukcje: Pobieranie danych ze schowka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: e29e71974abda3e6e57d22d9faef28e386ebeefd
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169904"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Instrukcje: Pobieranie danych ze schowka
<xref:System.Windows.Forms.Clipboard> Klasa zawiera metody, które służy do interakcji z funkcją Schowka systemu operacyjnego Windows. Wiele aplikacji używa Schowka jako tymczasowy repozytorium danych. Na przykład edytory użyć Schowka podczas operacji kopiowania i wklejania. Schowek jest również przydatne w przypadku przenoszenia informacji z jednej aplikacji do innej.  
  
 Niektóre aplikacje przechowują dane do Schowka w wielu formatach, aby zwiększyć liczbę inne aplikacje, które potencjalnie mogą używać danych. Format Schowka jest ciągiem, który identyfikuje format. Aplikacja, która używa formatu zidentyfikowanych można pobrać skojarzone dane do Schowka. <xref:System.Windows.Forms.DataFormats> Klasa udostępnia wstępnie zdefiniowany format nazw do użycia. Można również użyć własnych nazw formatu lub użyć typu obiektu jako jego format. Aby uzyskać informacje dotyczące dodawania danych do Schowka, zobacz [jak: Dodawanie danych do Schowka](how-to-add-data-to-the-clipboard.md).  
  
 Aby ustalić, czy Schowek zawiera dane w określonym formacie, użyj jednej z `Contains` *Format* metody lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Aby pobrać dane ze Schowka, użyj jednej z `Get` *Format* metody lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody. Te metody są nowością w programie .NET Framework 2.0.  
  
 Dostęp do danych ze Schowka za pomocą wersji starszej niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], użyj <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> — metoda i wywołać metodę zwracanego <xref:System.Windows.Forms.IDataObject>. Aby ustalić, czy określonego formatu jest dostępna w zwróconego obiektu, na przykład wywołać <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metody.  
  
> [!NOTE]
>  Wszystkie aplikacje oparte na Windows Udostępnianie Schowka systemu Windows. W związku z tym zawartość mogą ulec zmianie po przełączeniu do innej aplikacji.  
>   
>  <xref:System.Windows.Forms.Clipboard> Klasy należy używać tylko w wątkach ustawiany w trybie Jednowątkowego apartamentu jednego wątku. Aby użyć tej klasy, upewnij się, że Twoje `Main` metoda jest oznaczona atrybutem <xref:System.STAThreadAttribute> atrybutu.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Można pobrać danych ze Schowka w formacie jednej, wspólnej  
  
1. Użyj <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, lub <xref:System.Windows.Forms.Clipboard.GetText%2A> metody. Opcjonalnie można użyć odpowiedniego `Contains` *Format* metody, aby ustalić, czy dane są dostępne w określonym formacie. Te metody są dostępne tylko w programie .NET Framework 2.0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Można pobrać danych ze Schowka w niestandardowym formacie  
  
1. Użyj <xref:System.Windows.Forms.Clipboard.GetData%2A> metodę o nazwie formatu niestandardowego. Ta metoda jest dostępny tylko w programie .NET Framework 2.0.  
  
     Można również użyć wstępnie zdefiniowany format nazwy <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Można pobrać danych ze Schowka w wielu formatach  
  
1. Użyj <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metody. Należy użyć tej metody do pobierania danych ze Schowka w wersjach wcześniejszych niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)
- [Instrukcje: Dodawanie danych do Schowka](how-to-add-data-to-the-clipboard.md)
