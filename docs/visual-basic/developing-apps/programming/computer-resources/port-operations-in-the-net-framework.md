---
title: Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 10488f896ff7c6761e831d2a8af52249a19cf7d6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524387"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic

Dostęp do portów szeregowych komputera można uzyskać za pomocą klas .NET Framework w przestrzeni nazw <xref:System.IO.Ports?displayProperty=nameWithType>. Najważniejsze klasy, <xref:System.IO.Ports.SerialPort>, to struktura synchronicznych i opartych na zdarzeniach operacji we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego. Może być opakowany w obiekt <xref:System.IO.Stream>, dostępny za pomocą właściwości <xref:System.IO.Ports.SerialPort.BaseStream>. Zawijanie <xref:System.IO.Ports.SerialPort> w obiekcie <xref:System.IO.Stream> umożliwia dostęp do portu szeregowego przez klasy korzystające ze strumieni. Przestrzeń nazw zawiera wyliczenia, które upraszczają kontrolę portów szeregowych.

Najprostszym sposobem utworzenia obiektu <xref:System.IO.Ports.SerialPort> jest użycie metody <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.

> [!NOTE]
> Nie można użyć .NET Framework klas do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.

## <a name="enumerations"></a>Wyliczenia

W tej tabeli wymieniono główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:

|Wyliczenie|Opis|
|---|---|
|<xref:System.IO.Ports.Handshake>|Określa protokół kontroli używany podczas ustanawiania komunikacji portu szeregowego dla obiektu <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.Parity>|Określa bit parzystości dla obiektu <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialData>|Określa typ znaku, który został odebrany na porcie seryjnym obiektu <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialError>|Określa błędy występujące w obiekcie <xref:System.IO.Ports.SerialPort>|
|<xref:System.IO.Ports.SerialPinChange>|Określa typ zmiany, która wystąpiła w obiekcie <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.StopBits>|Określa liczbę bitów stopu używanych w obiekcie <xref:System.IO.Ports.SerialPort>.|

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Uzyskiwanie dostępu do portów komputera](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
