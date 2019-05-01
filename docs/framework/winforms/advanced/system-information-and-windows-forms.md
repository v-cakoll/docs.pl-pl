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
ms.openlocfilehash: eeb469dbf4553634aa50d0a9ea17e9b2464defb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934696"
---
# <a name="system-information-and-windows-forms"></a>Informacje o systemie i formularze systemu Windows
Czasami jest konieczne do zbierania informacji o komputerze, na którym aplikacja jest uruchomiona w celu podejmowania decyzji w kodzie. Na przykład Niewykluczone, że funkcja, która dotyczy tylko po podłączeniu do określonej domeny; w takim przypadku należałoby możliwość określenia domeny i wyłączyć funkcję, jeśli domena nie jest obecny.  
  
 Można używać w aplikacjach Windows Forms <xref:System.Windows.Forms.SystemInformation> klasę, aby określić kilka kwestii, o komputerze w czasie wykonywania. Poniższy przykład demonstruje użycie <xref:System.Windows.Forms.SystemInformation> klasy do pobrania <xref:System.Windows.Forms.SystemInformation.UserName%2A> i <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 Wszystkie elementy członkowskie <xref:System.Windows.Forms.SystemInformation> klasy są przeznaczone tylko do odczytu; nie można zmodyfikować ustawień użytkownika. Istnieje ponad 100 elementów członkowskich klasy, zwracanie informacji wszystkiego, co z wybranej liczby monitorów podłączony do komputera (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) odstępy między ikon w Eksploratorze Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> i <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Niektóre z bardziej użyteczny, członkowie <xref:System.Windows.Forms.SystemInformation> zawierają klasy <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, i <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SystemInformation>
- [Zarządzanie energią w formularzach Windows Forms](power-management-in-windows-forms.md)
