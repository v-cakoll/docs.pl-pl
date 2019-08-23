---
title: 'Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 20bc177ccf2646f79994553803568531233ea5c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935480"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)
Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do wstrzymania usługi administratora usług IIS na komputerze lokalnym.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do projektu do System. ServiceProcess. dll.  
  
- Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw. `Imports` Dodaj instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie. Aby uzyskać więcej informacji, zobacz Imports — [instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość<xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym. Aby odwoływać się do usług systemu Windows na innym <xref:System.ServiceProcess.ServiceController.MachineName%2A> komputerze, należy zmienić właściwość na nazwę tego komputera.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nie można wstrzymać usługi. (<xref:System.InvalidOperationException>)  
  
- Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Kontrolowanie usług na komputerze może być ograniczone przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> programu w celu ustawienia uprawnień <xref:System.ServiceProcess.ServiceControllerPermission>w.  
  
 Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> do ustawiania uprawnień <xref:System.Security.Permissions.SecurityPermission>w.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Instrukcje: Kontynuuj działanie usługi systemu Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
