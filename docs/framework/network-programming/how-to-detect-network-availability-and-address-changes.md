---
title: 'Instrukcje: wykrywanie dostępności sieci i zmian adresów'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: c0a4a492b06ac3be09d00779f97f1eb76d2690f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642636"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="ca827-102">Instrukcje: wykrywanie dostępności sieci i zmian adresów</span><span class="sxs-lookup"><span data-stu-id="ca827-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="ca827-103">W tym przykładzie pokazano, jak wykrywać zmiany w adresu sieciowego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ca827-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca827-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca827-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca827-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ca827-105">Compiling the Code</span></span>  
 <span data-ttu-id="ca827-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ca827-106">This example requires:</span></span>  
  
- <span data-ttu-id="ca827-107">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ca827-107">References to the **System.Net** namespace.</span></span>
