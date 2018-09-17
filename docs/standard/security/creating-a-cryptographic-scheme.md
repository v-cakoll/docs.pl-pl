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
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964387"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="4381f-102">Tworzenie schematu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="4381f-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="4381f-103">Można łączyć kryptograficznych składników .NET Framework do tworzenia różnych systemów do szyfrowania i odszyfrowywania danych.</span><span class="sxs-lookup"><span data-stu-id="4381f-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="4381f-104">Prosty schemat szyfrowania szyfrowanie i odszyfrowywanie danych może określić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4381f-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="4381f-105">Każda ze stron generowana jest para kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="4381f-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="4381f-106">Strony wymiany kluczy publicznych.</span><span class="sxs-lookup"><span data-stu-id="4381f-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="4381f-107">Każda ze stron generuje klucz tajny dla celów szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="4381f-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="4381f-108">Każda strona wysyła dane do drugiego i łączy klucz tajny drugiej strony z własną, w szczególności kolejności, aby utworzyć nowy klucz tajny.</span><span class="sxs-lookup"><span data-stu-id="4381f-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="4381f-109">Strony następnie zainicjuj konwersacji za pomocą szyfrowania symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="4381f-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="4381f-110">Tworzenie schematu kryptograficznego nie jest prostym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="4381f-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="4381f-111">Aby uzyskać więcej informacji na temat korzystania z szyfrowania, zobacz temat kryptografii w dokumentacji platformy SDK pod adresem http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="4381f-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4381f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4381f-112">See also</span></span>

- [<span data-ttu-id="4381f-113">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="4381f-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
