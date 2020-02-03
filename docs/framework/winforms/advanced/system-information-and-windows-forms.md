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
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="b2411-102">Informacje o systemie i formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b2411-102">System Information and Windows Forms</span></span>
<span data-ttu-id="b2411-103">Czasami konieczne jest zebranie informacji o komputerze, na którym działa aplikacja, aby podejmować decyzje w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b2411-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="b2411-104">Na przykład może istnieć funkcja, która ma zastosowanie tylko w przypadku połączenia z określoną domeną sieciową; w takim przypadku należy określić domenę i wyłączyć funkcję, jeśli domena nie jest obecna.</span><span class="sxs-lookup"><span data-stu-id="b2411-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="b2411-105">Aplikacje Windows Forms mogą korzystać z klasy <xref:System.Windows.Forms.SystemInformation> w celu określenia liczby rzeczy o komputerze w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b2411-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="b2411-106">Poniższy przykład ilustruje użycie klasy <xref:System.Windows.Forms.SystemInformation> do pobrania <xref:System.Windows.Forms.SystemInformation.UserName%2A> i <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="b2411-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
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
  
 <span data-ttu-id="b2411-107">Wszystkie elementy członkowskie klasy <xref:System.Windows.Forms.SystemInformation> są tylko do odczytu; nie można zmodyfikować ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b2411-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="b2411-108">Istnieje ponad 100 elementów członkowskich klasy, zwracając wszystkie informacje z liczby monitorów dołączonych do komputera (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) do odstępów ikon w Eksploratorze Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> i <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="b2411-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="b2411-109">Niektóre z bardziej użytecznych elementów członkowskich klasy <xref:System.Windows.Forms.SystemInformation> obejmują <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>i <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2411-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2411-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2411-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="b2411-111">Zarządzanie energią w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2411-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
