---
title: 'Instrukcje: wykrywanie dostępności sieci i zmian adresów'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c0357c4000a7efdb838a40f2f3f907c1dd313c58
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193125"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="a3749-102">Instrukcje: wykrywanie dostępności sieci i zmian adresów</span><span class="sxs-lookup"><span data-stu-id="a3749-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="a3749-103">W tym przykładzie pokazano, jak wykrywać zmiany w adresu sieciowego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3749-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3749-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3749-104">Example</span></span>  
  
```  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a3749-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a3749-105">Compiling the Code</span></span>  
 <span data-ttu-id="a3749-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a3749-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a3749-107">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a3749-107">References to the **System.Net** namespace.</span></span>
