---
title: Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 66b3729081540e8dede42556c58e44cd55b62666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584722"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
Są dostępne porty szeregowe komputera za pośrednictwem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klas w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw. Najważniejsze klasy <xref:System.IO.Ports.SerialPort>, dostarcza strukturę dla synchroniczne i sterowane zdarzeniami we/wy, dostępu do numeru pin i podział stanów i dostęp do właściwości szeregowego sterownika. Może być ujęte w <xref:System.IO.Stream> obiektu dostępny za pośrednictwem <xref:System.IO.Ports.SerialPort.BaseStream> właściwości. Zawijanie <xref:System.IO.Ports.SerialPort> w <xref:System.IO.Stream> obiekt umożliwia portu szeregowego były dostępne dla klasy, które używają strumieni. Ta przestrzeń nazw obejmuje wyliczenia, które ułatwiają kontrolę nad porty szeregowe.  
  
 Najprostszym sposobem tworzenia <xref:System.IO.Ports.SerialPort> obiekt jest za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.  
  
> [!NOTE]
>  Nie można użyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy bezpośredni dostęp do innych portów, takich jak porty równoległe, portów USB i tak dalej.  
  
## <a name="enumerations"></a>Wyliczenia  
 W tej tabeli wymieniono i opisano główny wyliczenia, używane do uzyskiwania dostępu do portu szeregowego:  
  
|Wyliczenie|Opis|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Określa używany podczas ustanawiania komunikacji portu szeregowego, dla protokołu sterowania <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.Parity>|Określa bit parzystości dla <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.SerialData>|Określa typ znak, który został odebrany w portu szeregowego <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.SerialError>|Określa błędów występujących na <xref:System.IO.Ports.SerialPort> obiektu|  
|<xref:System.IO.Ports.SerialPinChange>|Określa typ zmiany, który wystąpił na <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.StopBits>|Określa liczbę bitów stopu używane na <xref:System.IO.Ports.SerialPort> obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Uzyskiwanie dostępu do portów komputera](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
