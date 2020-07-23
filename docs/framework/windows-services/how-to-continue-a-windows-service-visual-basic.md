---
title: 'Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)'
description: Przeczytaj, jak używać składnika ServiceController do kontynuowania usługi systemu Windows (na przykład usługi administratora usług IIS) na komputerze lokalnym z Visual Basic.
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
ms.openlocfilehash: 2a04e330ea7dc37552053b2a7915909c011727f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925790"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Instrukcje: Kontynuowanie usługi systemu Windows (Visual Basic)
Ten przykład używa <xref:System.ServiceProcess.ServiceController> składnika do kontynuowania usługi administratora usług IIS na komputerze lokalnym.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym windows > usług systemu Windows**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołanie do projektu do System.serviceprocess.dll.  
  
- Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw. Dodaj `Imports` instrukcję, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest domyślnie komputerem lokalnym. Aby odwoływać się do usług systemu Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość na nazwę tego komputera.  
  
 Nie można wywołać <xref:System.ServiceProcess.ServiceController.Continue%2A> metody w usłudze do momentu, gdy kontroler usług nie ma stanu <xref:System.ServiceProcess.ServiceControllerStatus.Paused> .  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nie można wznowić usługi. (<xref:System.InvalidOperationException>)  
  
- Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Kontrola usług na komputerze może być ograniczona przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> wyliczenia, aby ustawić uprawnienia w <xref:System.ServiceProcess.ServiceControllerPermission> klasie.  
  
 Dostęp do informacji o usłudze może być ograniczony przy użyciu <xref:System.Security.Permissions.PermissionState> wyliczenia w celu ustawienia uprawnień w <xref:System.Security.Permissions.SecurityPermission> klasie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [Instrukcje: Wstrzymywanie usługi systemu Windows (Visual Basic)](how-to-pause-a-windows-service-visual-basic.md)
