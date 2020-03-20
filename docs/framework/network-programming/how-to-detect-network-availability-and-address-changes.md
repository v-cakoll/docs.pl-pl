---
title: 'Instrukcje: wykrywanie dostępności sieci i zmian adresów'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: 9e265a97d339da59bb9d0af6ab6757e16af00e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70894964"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="14094-102">Instrukcje: wykrywanie dostępności sieci i zmian adresów</span><span class="sxs-lookup"><span data-stu-id="14094-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="14094-103">W tym przykładzie pokazano, jak wykryć zmiany w adresie sieciowym interfejsu.</span><span class="sxs-lookup"><span data-stu-id="14094-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14094-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="14094-104">Example</span></span>  
  
```csharp
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14094-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="14094-105">Compiling the Code</span></span>  
 <span data-ttu-id="14094-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="14094-106">This example requires:</span></span>  
  
- <span data-ttu-id="14094-107">Odwołania do **System.Net** obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="14094-107">References to the **System.Net** namespace.</span></span>
