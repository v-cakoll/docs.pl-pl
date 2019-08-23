---
title: Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 936ff4c861444d3a971b38fd7b2a0af38b19494b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916604"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="edce9-102">Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edce9-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="edce9-103">Dostęp do portów szeregowych komputera można uzyskać za pomocą klas .NET Framework w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="edce9-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="edce9-104">Najważniejszym klasą <xref:System.IO.Ports.SerialPort>,,, jest struktura synchronicznych i opartych na zdarzeniach operacji we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego.</span><span class="sxs-lookup"><span data-stu-id="edce9-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="edce9-105">Może być opakowany w <xref:System.IO.Stream> obiekt, dostępny <xref:System.IO.Ports.SerialPort.BaseStream> za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="edce9-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="edce9-106"><xref:System.IO.Ports.SerialPort> Zawijanie<xref:System.IO.Stream> w obiekcie umożliwia dostęp do portu szeregowego przez klasy, które używają strumieni.</span><span class="sxs-lookup"><span data-stu-id="edce9-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="edce9-107">Przestrzeń nazw zawiera wyliczenia, które upraszczają kontrolę portów szeregowych.</span><span class="sxs-lookup"><span data-stu-id="edce9-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="edce9-108">Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiektu jest <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> użycie metody.</span><span class="sxs-lookup"><span data-stu-id="edce9-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edce9-109">Nie można użyć .NET Framework klas do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="edce9-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="edce9-110">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="edce9-110">Enumerations</span></span>  
 <span data-ttu-id="edce9-111">W tej tabeli wymieniono główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:</span><span class="sxs-lookup"><span data-stu-id="edce9-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="edce9-112">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="edce9-112">Enumeration</span></span>|<span data-ttu-id="edce9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="edce9-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="edce9-114">Określa protokół kontroli używany do ustanawiania komunikacji portu szeregowego dla <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="edce9-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="edce9-115">Określa bit parzystości dla <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="edce9-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="edce9-116">Określa typ znaku, który został odebrany przez port <xref:System.IO.Ports.SerialPort> szeregowy obiektu.</span><span class="sxs-lookup"><span data-stu-id="edce9-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="edce9-117">Określa błędy występujące w <xref:System.IO.Ports.SerialPort> obiekcie</span><span class="sxs-lookup"><span data-stu-id="edce9-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="edce9-118">Określa typ zmiany, która wystąpiła w <xref:System.IO.Ports.SerialPort> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="edce9-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="edce9-119">Określa liczbę bitów stopu używanych w <xref:System.IO.Ports.SerialPort> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="edce9-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edce9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edce9-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="edce9-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="edce9-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
