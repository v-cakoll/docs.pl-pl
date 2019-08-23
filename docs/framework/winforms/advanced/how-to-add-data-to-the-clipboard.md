---
title: 'Instrukcje: Dodawanie danych do schowka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: d4afcd6ce942d1cd2286e3f393ce61436821bb3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955123"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Instrukcje: Dodawanie danych do schowka
<xref:System.Windows.Forms.Clipboard> Klasa zawiera metody, których można użyć do współdziałania z funkcją Schowka systemu operacyjnego Windows. Wiele aplikacji używa Schowka jako tymczasowego repozytorium dla danych. Na przykład edytory tekstów używają schowka podczas operacji wycinania i wklejania. Schowek jest również przydatny do transferowania danych z jednej aplikacji do innej.  
  
 Po dodaniu danych do schowka można wskazać format danych, aby inne aplikacje mogły rozpoznać dane, jeśli mogą korzystać z tego formatu. Możesz również dodać dane do Schowka w wielu różnych formatach, aby zwiększyć liczbę innych aplikacji, które mogą potencjalnie korzystać z danych.  
  
 Format schowka to ciąg identyfikujący format, dzięki czemu Aplikacja korzystająca z tego formatu może pobrać skojarzone dane. <xref:System.Windows.Forms.DataFormats> Klasa zawiera wstępnie zdefiniowane nazwy formatów do użycia. Możesz również użyć własnych nazw formatu lub użyć typu obiektu jako formatu.  
  
 Aby dodać dane do Schowka w jednym lub wielu formatach, użyj <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metody. Można przekazać dowolny obiekt do tej metody, ale aby dodać dane w wielu formatach, należy najpierw dodać dane do oddzielnego obiektu zaprojektowanego do pracy z wieloma formatami. Zwykle dane zostaną dodane do <xref:System.Windows.Forms.DataObject>, ale można użyć dowolnego typu, który <xref:System.Windows.Forms.IDataObject> implementuje interfejs.  
  
 W .NET Framework 2,0 można dodać dane bezpośrednio do schowka przy użyciu nowych metod, które ułatwiają wykonywanie podstawowych zadań w Schowku. Te metody są używane podczas pracy z danymi w jednym, wspólnym formacie, takim jak tekst.  
  
> [!NOTE]
> Wszystkie aplikacje oparte na systemie Windows korzystają ze schowka. W związku z tym zawartość może ulec zmianie po przełączeniu do innej aplikacji.  
>   
>  <xref:System.Windows.Forms.Clipboard> Klasy można używać tylko w wątkach ustawionych na tryb Single Thread Apartment (STA). Aby użyć tej klasy, należy się upewnić, że `Main` Metoda jest oznaczona <xref:System.STAThreadAttribute> przy użyciu atrybutu.  
>   
>  Obiekt musi być możliwy do serializacji, aby można go było umieścić w Schowku. Aby można było serializować typ, oznacz go <xref:System.SerializableAttribute> atrybutem. Jeśli przekazanie obiektu, którego nie można serializować, do metody Schowka, metoda zakończy się niepowodzeniem bez zgłaszania wyjątku. Aby uzyskać więcej informacji na temat serializacji <xref:System.Runtime.Serialization>, zobacz.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Aby dodać dane do Schowka w jednym, wspólnym formacie  
  
1. Użyj metody <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A> ,,<xref:System.Windows.Forms.Clipboard.SetImage%2A>lub .<xref:System.Windows.Forms.Clipboard.SetText%2A> <xref:System.Windows.Forms.Clipboard.SetAudio%2A> Te metody są dostępne tylko w .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Aby dodać dane do Schowka w formacie niestandardowym  
  
1. <xref:System.Windows.Forms.Clipboard.SetData%2A> Użyj metody z niestandardową nazwą formatu. Ta metoda jest dostępna tylko w .NET Framework 2,0.  
  
     Można również użyć wstępnie zdefiniowanych nazw formatu przy użyciu <xref:System.Windows.Forms.Clipboard.SetData%2A> metody. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Aby dodać dane do Schowka w wielu formatach  
  
1. Użyj metody i przekaż <xref:System.Windows.Forms.DataObject> , która zawiera dane. <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> Ta metoda służy do dodawania danych do Schowka w wersjach wcześniejszych niż .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)
- [Instrukcje: Pobieranie danych ze schowka](how-to-retrieve-data-from-the-clipboard.md)
