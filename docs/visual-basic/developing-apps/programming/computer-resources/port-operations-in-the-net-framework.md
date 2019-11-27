---
title: Operacje związane z portem w oprogramowaniu .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345504"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="c6e6f-102">Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6e6f-102">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="c6e6f-103">Dostęp do portów szeregowych komputera można uzyskać za pomocą klas .NET Framework w przestrzeni nazw <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c6e6f-104">Najważniejsze klasy, <xref:System.IO.Ports.SerialPort>, to struktura synchronicznych i opartych na zdarzeniach operacji we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="c6e6f-105">Może być opakowany w obiekt <xref:System.IO.Stream>, dostępny za pomocą właściwości <xref:System.IO.Ports.SerialPort.BaseStream>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="c6e6f-106">Zawijanie <xref:System.IO.Ports.SerialPort> w obiekcie <xref:System.IO.Stream> umożliwia dostęp do portu szeregowego przez klasy korzystające ze strumieni.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="c6e6f-107">Przestrzeń nazw zawiera wyliczenia, które upraszczają kontrolę portów szeregowych.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="c6e6f-108">Najprostszym sposobem utworzenia obiektu <xref:System.IO.Ports.SerialPort> jest użycie metody <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e6f-109">Nie można użyć .NET Framework klas do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="c6e6f-110">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c6e6f-110">Enumerations</span></span>

<span data-ttu-id="c6e6f-111">W tej tabeli wymieniono główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:</span><span class="sxs-lookup"><span data-stu-id="c6e6f-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="c6e6f-112">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c6e6f-112">Enumeration</span></span>|<span data-ttu-id="c6e6f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c6e6f-113">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="c6e6f-114">Określa protokół kontroli używany podczas ustanawiania komunikacji portu szeregowego dla obiektu <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="c6e6f-115">Określa bit parzystości dla obiektu <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="c6e6f-116">Określa typ znaku, który został odebrany na porcie seryjnym obiektu <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="c6e6f-117">Określa błędy występujące w obiekcie <xref:System.IO.Ports.SerialPort></span><span class="sxs-lookup"><span data-stu-id="c6e6f-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="c6e6f-118">Określa typ zmiany, która wystąpiła w obiekcie <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="c6e6f-119">Określa liczbę bitów stopu używanych w obiekcie <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="c6e6f-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c6e6f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6e6f-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="c6e6f-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="c6e6f-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
