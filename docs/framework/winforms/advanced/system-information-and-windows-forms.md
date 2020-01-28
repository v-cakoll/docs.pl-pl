---
title: Informacje o systemie
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
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732590"
---
# <a name="system-information-and-windows-forms"></a>Informacje o systemie i formularze systemu Windows
Czasami konieczne jest zebranie informacji o komputerze, na którym działa aplikacja, aby podejmować decyzje w kodzie. Na przykład może istnieć funkcja, która ma zastosowanie tylko w przypadku połączenia z określoną domeną sieciową; w takim przypadku należy określić domenę i wyłączyć funkcję, jeśli domena nie jest obecna.  
  
 Aplikacje Windows Forms mogą korzystać z klasy <xref:System.Windows.Forms.SystemInformation> w celu określenia liczby rzeczy o komputerze w czasie wykonywania. Poniższy przykład ilustruje użycie klasy <xref:System.Windows.Forms.SystemInformation> do pobrania <xref:System.Windows.Forms.SystemInformation.UserName%2A> i <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 Wszystkie elementy członkowskie klasy <xref:System.Windows.Forms.SystemInformation> są tylko do odczytu; nie można zmodyfikować ustawień użytkownika. Istnieje ponad 100 elementów członkowskich klasy, zwracając wszystkie informacje z liczby monitorów dołączonych do komputera (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) do odstępów ikon w Eksploratorze Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> i <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Niektóre z bardziej użytecznych elementów członkowskich klasy <xref:System.Windows.Forms.SystemInformation> obejmują <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>i <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SystemInformation>
- [Zarządzanie energią w formularzach Windows Forms](power-management-in-windows-forms.md)
