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
ms.openlocfilehash: 3ef3741ef5cec720c2fb285c9aa60d610acc0be9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321656"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="881b5-102">Tworzenie schematu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="881b5-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="881b5-103">Można łączyć kryptograficznych składników .NET Framework do tworzenia różnych systemów do szyfrowania i odszyfrowywania danych.</span><span class="sxs-lookup"><span data-stu-id="881b5-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="881b5-104">Prosty schemat szyfrowania szyfrowanie i odszyfrowywanie danych może określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="881b5-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="881b5-105">Każda ze stron generowana jest para kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="881b5-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="881b5-106">Strony wymiany kluczy publicznych.</span><span class="sxs-lookup"><span data-stu-id="881b5-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="881b5-107">Każda ze stron generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="881b5-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="881b5-108">Każda strona wysyła dane do drugiego i łączy klucz tajny drugiej strony z własną, w szczególności kolejności, aby utworzyć nowy klucz tajny.</span><span class="sxs-lookup"><span data-stu-id="881b5-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="881b5-109">Strony następnie zainicjuj konwersacji za pomocą szyfrowania symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="881b5-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="881b5-110">Tworzenie schematu kryptograficznego nie jest prostym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="881b5-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="881b5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="881b5-111">See also</span></span>

- [<span data-ttu-id="881b5-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="881b5-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
