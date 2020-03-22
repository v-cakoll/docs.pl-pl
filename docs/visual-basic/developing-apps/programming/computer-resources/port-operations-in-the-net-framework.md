---
title: Operacje związane z portem w oprogramowaniu .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345504"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="2c6de-102">Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c6de-102">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="2c6de-103">Dostęp do portów szeregowych komputera można uzyskać za <xref:System.IO.Ports?displayProperty=nameWithType> pośrednictwem klas .NET Framework w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="2c6de-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="2c6de-104">Najważniejsza klasa <xref:System.IO.Ports.SerialPort>, zapewnia ramy dla synchronicznych i opartych na zdarzeniach we/wy, dostęp do stanów przypięcia i przerwania oraz dostęp do właściwości sterownika szeregowego.</span><span class="sxs-lookup"><span data-stu-id="2c6de-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="2c6de-105">Może być zawinięty <xref:System.IO.Stream> w obiekt, <xref:System.IO.Ports.SerialPort.BaseStream> dostępny za pośrednictwem właściwości.</span><span class="sxs-lookup"><span data-stu-id="2c6de-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="2c6de-106"><xref:System.IO.Ports.SerialPort> Zawijanie <xref:System.IO.Stream> w obiekcie umożliwia dostęp do portu szeregowego przez klasy, które używają strumieni.</span><span class="sxs-lookup"><span data-stu-id="2c6de-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="2c6de-107">Obszar nazw zawiera wyliczenia, które upraszczają kontrolę nad portami szeregowymi.</span><span class="sxs-lookup"><span data-stu-id="2c6de-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="2c6de-108">Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiektu jest <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="2c6de-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="2c6de-109">Nie można używać klas programu .NET Framework do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2c6de-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="2c6de-110">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2c6de-110">Enumerations</span></span>

<span data-ttu-id="2c6de-111">W tej tabeli wymieniono i opisano główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:</span><span class="sxs-lookup"><span data-stu-id="2c6de-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="2c6de-112">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2c6de-112">Enumeration</span></span>|<span data-ttu-id="2c6de-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2c6de-113">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="2c6de-114">Określa protokół sterowania używany do ustanawiania komunikacji <xref:System.IO.Ports.SerialPort> portu szeregowego dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c6de-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="2c6de-115">Określa bit parzystości <xref:System.IO.Ports.SerialPort> dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c6de-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="2c6de-116">Określa typ znaku odebranego na porcie szeregowym <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c6de-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="2c6de-117">Określa błędy występujące w <xref:System.IO.Ports.SerialPort> obiekcie</span><span class="sxs-lookup"><span data-stu-id="2c6de-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="2c6de-118">Określa typ zmiany, która wystąpiła <xref:System.IO.Ports.SerialPort> w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="2c6de-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="2c6de-119">Określa liczbę bitów zatrzymania używanych <xref:System.IO.Ports.SerialPort> w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="2c6de-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2c6de-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c6de-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="2c6de-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="2c6de-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
