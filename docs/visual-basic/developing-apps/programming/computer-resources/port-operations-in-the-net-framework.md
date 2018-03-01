---
title: "Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77b8a464f2f64f701a5b99690756c0f22a410064
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
