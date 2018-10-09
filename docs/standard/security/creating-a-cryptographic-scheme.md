---
title: Tworzenie schematu kryptograficznego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51d07fadcf359c2b44f22ca9868d0f12e24b80c5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873125"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="3b162-102">Tworzenie schematu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="3b162-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="3b162-103">Można łączyć kryptograficznych składników .NET Framework do tworzenia różnych systemów do szyfrowania i odszyfrowywania danych.</span><span class="sxs-lookup"><span data-stu-id="3b162-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="3b162-104">Prosty schemat szyfrowania szyfrowanie i odszyfrowywanie danych może określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="3b162-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="3b162-105">Każda ze stron generowana jest para kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="3b162-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="3b162-106">Strony wymiany kluczy publicznych.</span><span class="sxs-lookup"><span data-stu-id="3b162-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="3b162-107">Każda ze stron generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="3b162-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="3b162-108">Każda strona wysyła dane do drugiego i łączy klucz tajny drugiej strony z własną, w szczególności kolejności, aby utworzyć nowy klucz tajny.</span><span class="sxs-lookup"><span data-stu-id="3b162-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="3b162-109">Strony następnie zainicjuj konwersacji za pomocą szyfrowania symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="3b162-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="3b162-110">Tworzenie schematu kryptograficznego nie jest prostym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="3b162-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3b162-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b162-111">See also</span></span>

- [<span data-ttu-id="3b162-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="3b162-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
