---
title: 'Porady: wykrywanie dostępności sieci i rozwiąż zmiany'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9056c8b2ecf18c4a57d356e7c9698984df1558eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396262"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="b9bb3-102">Porady: wykrywanie dostępności sieci i rozwiąż zmiany</span><span class="sxs-lookup"><span data-stu-id="b9bb3-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="b9bb3-103">Ten przykład przedstawia sposób wykrywania zmian adresu sieciowego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b9bb3-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9bb3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bb3-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9bb3-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b9bb3-105">Compiling the Code</span></span>  
 <span data-ttu-id="b9bb3-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b9bb3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b9bb3-107">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bb3-107">References to the **System.Net** namespace.</span></span>
