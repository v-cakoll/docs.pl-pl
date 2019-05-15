---
title: 'Instrukcje: Obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
ms.openlocfilehash: f2fb48e07243694b14904b240bdcb0739175c2fc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593528"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Instrukcje: Obsługa międzyoperacyjności w modelu COM za pomocą wyświetlania formularzy systemu Windows przy użyciu metody ShowDialog
Można rozwiązać problemy ze współdziałaniem Component Object Model (COM) za pomocą wyświetlania formularza Windows w pętli komunikatów .NET Framework, która została utworzona przy użyciu <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.  
  
 Aby działać poprawnie z modelu COM aplikacji klienckiej formularza, należy uruchom go na pętli komunikatów Windows Forms. Aby to zrobić, użyj jednej z następujących metod:  
  
- Użyj <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza Windows;  
  
- Wyświetlania każdego formularza Windows w oddzielnym wątku. Aby uzyskać więcej informacji, zobacz [jak: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza Windows w jego własnym wątku](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Procedura  
 Za pomocą <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda może być Najprostszym sposobem wyświetlenia formularza w pętli komunikatów .NET Framework, ponieważ wszystkie podejścia wymaga co najmniej kod w celu zaimplementowania.  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Metoda wstrzymuje pętli komunikatów dla niezarządzanych aplikacji i zostanie wyświetlony formularz jako okno dialogowe. Ponieważ pętli komunikatów dla aplikacji hosta zostało zawieszone, <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda tworzy nowy pętli komunikatów .NET Framework do przetwarzania komunikatów z formularza.  
  
 Wadą korzystania <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metoda to, że formularz zostanie otwarty jako modalne okno dialogowe. To zachowanie blokowanie żadnego interfejsu użytkownika (UI) w aplikacji wywołującej, gdy formularz Windows jest otwarty. Przy zamykaniu formularza zamyka pętli komunikatów dla .NET Framework i pętli komunikatów dla starszych aplikacji ponownym uruchomieniu.  
  
 Można utworzyć bibliotekę klas w formularzach Windows, który ma metodę, aby wyświetlić formularz, a następnie utworzyć bibliotekę klas dla współdziałania z modelem COM. Możesz użyć tego pliku biblioteki DLL z języka Visual Basic 6.0 lub Microsoft Foundation Classes (MFC), a przy użyciu dowolnego z tych środowisk może wywołać <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodę w celu wyświetlenia formularza.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Do obsługi COM interop poprzez wyświetlanie formularza systemu windows za pomocą ShowDialog — metoda  
  
- Zastąp wszystkie wywołania do <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> metody za pomocą wywołania <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metody w składniku .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników .NET Framework modelowi COM](../../interop/exposing-dotnet-components-to-com.md)
- [Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza Windows w jego własnym wątku](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
- [Formularze Windows Forms i niezarządzane aplikacje](windows-forms-and-unmanaged-applications.md)
