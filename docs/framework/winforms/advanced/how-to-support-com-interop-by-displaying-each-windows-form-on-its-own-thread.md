---
title: 'Porady: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f5d8a0351fc206aad9d88f9ca3f7c930ff853ff7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Porady: obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku
Można rozwiązać problemy współdziałania COM za pomocą wyświetlania formularza na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pętli komunikatów, które można tworzyć przy użyciu <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.  
  
 Aby poprawnie z aplikacji klienckiej COM służbowy formularza systemu Windows, należy uruchomić formularza w pętli komunikatów formularzy systemu Windows. Aby to zrobić, użyj jednej z następujących metod:  
  
-   Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Obsługa międzyoperacyjności z modelem COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Wyświetlania każdego formularza systemu Windows w oddzielnym wątku.  
  
 Brak kompleksową obsługę tej funkcji w programie Visual Studio.  
  
 Zobacz też [wskazówki: Obsługa międzyoperacyjności z modelem COM. wyświetlania każdego formularza systemu Windows w jego własnym wątku w](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób wyświetlania formularza w oddzielnym wątku i wywołanie <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodę, aby uruchomić przekazywanie komunikatów formularzy systemu Windows na tym wątku. Aby użyć tej metody, należy kierować wezwań do formularza z niezarządzanych aplikacji przy użyciu <xref:System.Windows.Forms.Control.Invoke%2A> metody.  
  
 Ta metoda wymaga każde wystąpienie formularza działa przy użyciu własnego pętli komunikatów w jego własnym wątku. Nie może mieć więcej niż jeden pętli komunikatów uruchomiona na wątek. W związku z tym nie można zmienić pętli komunikatów aplikacji klienckiej. Jednak można zmodyfikować [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] składnika można rozpocząć nowego wątku, który używa własnego pętli komunikatów.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Kompiluj `COMForm`, `Form1`, i `FormManager` typów w zestawie o nazwie `COMWinform.dll`. Zarejestrować zestawu dla międzyoperacyjności z modelem COM za pomocą jednej z metod opisanych w [pakowanie zestawu dla modelu COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Można teraz używać zestawu i jego odpowiedni plik biblioteki (.tlb) typu w niezarządzanych aplikacji. Na przykład można użyć biblioteki typów jako odwołanie w Visual Basic 6.0 projekt wykonywalny.  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie składników .NET Framework modelowi COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Pakowanie zestawu dla modelu COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Rejestrowanie zestawów do użycia z modelem COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Instrukcje: obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
