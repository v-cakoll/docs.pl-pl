---
title: Tworzenie schematu kryptograficznego
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e3c4a832f70fae7808bf71016cb9f6648332f01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="3f107-102">Tworzenie schematu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="3f107-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="3f107-103">Do tworzenia różnych programów do szyfrowania i odszyfrowywania danych można łączyć kryptograficznych składników platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3f107-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="3f107-104">Proste schematu kryptograficznego do szyfrowania i odszyfrowywania danych może określać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3f107-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="3f107-105">Każda strona generuje pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="3f107-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="3f107-106">Strony wymiany kluczy publicznych.</span><span class="sxs-lookup"><span data-stu-id="3f107-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="3f107-107">Każda strona generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje klucz nowo utworzony przy użyciu klucza publicznego drugiego.</span><span class="sxs-lookup"><span data-stu-id="3f107-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="3f107-108">Strony wysyła dane do innych i łączy klucz tajny drugiego z własnej, w szczególności kolejność, aby utworzyć nowy klucz tajny.</span><span class="sxs-lookup"><span data-stu-id="3f107-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="3f107-109">Strony inicjuje konwersację za pomocą szyfrowania symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="3f107-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="3f107-110">Tworzenie schematu kryptograficznego manipulacji nie jest prosta.</span><span class="sxs-lookup"><span data-stu-id="3f107-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="3f107-111">Aby uzyskać więcej informacji na temat używania kryptografii zobacz temat kryptografii w dokumentacji zestawu SDK platformy w http://msdn.microsoft.com/library/.</span><span class="sxs-lookup"><span data-stu-id="3f107-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f107-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f107-112">See Also</span></span>  
 [<span data-ttu-id="3f107-113">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="3f107-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
