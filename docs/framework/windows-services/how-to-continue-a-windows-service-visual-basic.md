---
title: 'Porady: kontynuowanie usług systemu Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: 255dccfb74eced63ffbeff7ef567083a504cc6da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108384"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Porady: kontynuowanie usług systemu Windows (Visual Basic)
W tym przykładzie użyto <xref:System.ServiceProcess.ServiceController> składnika, aby kontynuować Administrator usług IIS na komputerze lokalnym.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu, znajduje się w **systemu operacyjnego Windows > usług Windows**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania projektu do System.serviceprocess.dll.  
  
-   Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw. Dodaj `Imports` instrukcji, jeśli użytkownik są nie pełni kwalifikujących się nazwy elementów członkowskich w kodzie. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasa jest na komputerze lokalnym domyślnie. Aby odwoływać się do usługi Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> właściwość na nazwę tego komputera.  
  
 Nie można wywołać <xref:System.ServiceProcess.ServiceController.Continue%2A> metody dla usługi, dopóki nie zostanie stan kontrolera usługi <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie można wznowić usługi. (<xref:System.InvalidOperationException>)  
  
-   Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Może być ograniczana kontroli usług na komputerze przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> wyliczeniu, aby ustawić uprawnienia w <xref:System.ServiceProcess.ServiceControllerPermission> klasy.  
  
 Dostęp do informacji o usłudze może być ograniczana przy użyciu <xref:System.Security.Permissions.PermissionState> wyliczeniu, aby ustawić uprawnienia w <xref:System.Security.Permissions.SecurityPermission> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [Instrukcje: wstrzymywanie usług systemu Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
