---
title: 'Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 39a9793f3046960032da32795e60314ea05a00fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779057"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku
Można rozwiązać problemy ze współdziałaniem COM za pomocą wyświetlania formularza w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, który można utworzyć za pomocą <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.  
  
 Aby dzieło formularza Windows poprawnie z modelu COM aplikacji klienckiej, należy uruchomić formularza na pętli komunikatów Windows Forms. Aby to zrobić, użyj jednej z następujących metod:  
  
- Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza Windows. Aby uzyskać więcej informacji, zobacz [jak: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania formularza Windows, za pomocą metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md).  
  
- Wyświetlania każdego formularza Windows w oddzielnym wątku.  
  
 Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.  
  
 Zobacz też [instruktażu: Obsługiwanie COM Interop poprzez wyświetlanie każdego formularzu Windows w jego własnym wątku](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób wyświetlania formularza w oddzielnym wątku i wywołania <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodę, aby uruchomić pompy komunikatów formularzy Windows w tym wątku. Aby użyć tej metody, należy kierować wszelkie wywołania do formularza z niezarządzanych aplikacji przy użyciu <xref:System.Windows.Forms.Control.Invoke%2A> metody.  
  
 Takie podejście wymaga każde wystąpienie formularza działa przy użyciu własnej pętli komunikatów w jego własnym wątku. Nie może mieć więcej niż jeden pętli komunikatów uruchomiona na wątek. W związku z tym nie można zmienić pętli komunikatów dla aplikacji klienckiej. Jednakże, możesz zmodyfikować [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] składnika można rozpocząć nowego wątku, która używa pętli komunikatów dla własnej.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Skompilować `COMForm`, `Form1`, i `FormManager` typów w zestawie o nazwie `COMWinform.dll`. Zarejestrować zestaw do współdziałania z modelem COM przy użyciu jednej z metod opisanych w [pakowanie zestawu dla modelu COM](../../interop/packaging-an-assembly-for-com.md). Można teraz używać zestawu i jego odpowiedni plik biblioteki (.tlb) typu w aplikacjach niezarządzanych. Na przykład można użyć biblioteki typów jako odwołania w projekcie języka Visual Basic 6.0 pliku wykonywalnego.  
  
## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników .NET Framework modelowi COM](../../interop/exposing-dotnet-components-to-com.md)
- [Pakowanie zestawu dla modelu COM](../../interop/packaging-an-assembly-for-com.md)
- [Rejestrowanie zestawów do użycia z modelem COM](../../interop/registering-assemblies-with-com.md)
- [Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania formularza Windows, za pomocą ShowDialog — metoda](com-interop-by-displaying-a-windows-form-shadow.md)
- [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](windows-forms-and-unmanaged-applications-overview.md)
