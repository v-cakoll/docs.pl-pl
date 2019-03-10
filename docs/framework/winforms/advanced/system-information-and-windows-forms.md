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
ms.openlocfilehash: d8efb783fcb5bcbe9c4ee99bc784e27a1aebb0cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707667"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="388e0-102">Informacje o systemie i formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="388e0-102">System Information and Windows Forms</span></span>
<span data-ttu-id="388e0-103">Czasami jest konieczne do zbierania informacji o komputerze, na którym aplikacja jest uruchomiona w celu podejmowania decyzji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="388e0-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="388e0-104">Na przykład Niewykluczone, że funkcja, która dotyczy tylko po podłączeniu do określonej domeny; w takim przypadku należałoby możliwość określenia domeny i wyłączyć funkcję, jeśli domena nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="388e0-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="388e0-105">Można używać w aplikacjach Windows Forms <xref:System.Windows.Forms.SystemInformation> klasę, aby określić kilka kwestii, o komputerze w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="388e0-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="388e0-106">Poniższy przykład demonstruje użycie <xref:System.Windows.Forms.SystemInformation> klasy do pobrania <xref:System.Windows.Forms.SystemInformation.UserName%2A> i <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="388e0-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
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
  
 <span data-ttu-id="388e0-107">Wszystkie elementy członkowskie <xref:System.Windows.Forms.SystemInformation> klasy są przeznaczone tylko do odczytu; nie można zmodyfikować ustawień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="388e0-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="388e0-108">Istnieje ponad 100 elementów członkowskich klasy, zwracanie informacji wszystkiego, co z wybranej liczby monitorów podłączony do komputera (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) odstępy między ikon w Eksploratorze Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> i <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="388e0-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="388e0-109">Niektóre z bardziej użyteczny, członkowie <xref:System.Windows.Forms.SystemInformation> zawierają klasy <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, i <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="388e0-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388e0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="388e0-110">See also</span></span>
- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="388e0-111">Zarządzanie energią w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="388e0-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
