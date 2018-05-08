---
title: Informacje o systemie i formularze systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: 727bcc53750081ae2d957527332ed3199c7d8e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="system-information-and-windows-forms"></a>Informacje o systemie i formularze systemu Windows
Czasami jest to konieczne zebrać informacje dotyczące komputera, na którym aplikacja jest uruchomiona na celu podejmowanie decyzji w kodzie. Na przykład może być funkcję, która dotyczy tylko po podłączeniu do określonej domeny; w takim przypadku należy określić domeny i wyłączenie tej funkcji, jeśli domena nie jest obecny.  
  
 Można użyć aplikacji Windows Forms <xref:System.Windows.Forms.SystemInformation> klasę, aby określić liczbę elementów o komputerze w czasie wykonywania. W poniższym przykładzie pokazano, za pomocą <xref:System.Windows.Forms.SystemInformation> klasy można pobrać <xref:System.Windows.Forms.SystemInformation.UserName%2A> i <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 Wszystkie elementy członkowskie <xref:System.Windows.Forms.SystemInformation> klasy są tylko do odczytu; nie można zmodyfikować ustawień użytkownika. Istnieje ponad 100 elementów członkowskich klasy, zwracanie informacji wszystkie z wybranej liczby monitorów podłączonych do komputera (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) do odstępy ikony w Eksploratorze Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> i <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Niektóre przydatne bardziej członków <xref:System.Windows.Forms.SystemInformation> obejmują klasy <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, i <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SystemInformation>  
 [Zarządzanie energią w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
