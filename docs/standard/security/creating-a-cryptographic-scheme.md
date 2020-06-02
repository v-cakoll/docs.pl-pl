---
title: Tworzenie schematu kryptograficznego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288423"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="c5da4-102">Tworzenie schematu kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="c5da4-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="c5da4-103">Składniki kryptograficzne .NET Framework można łączyć w celu tworzenia różnych schematów do szyfrowania i odszyfrowywania danych.</span><span class="sxs-lookup"><span data-stu-id="c5da4-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="c5da4-104">Prosty schemat kryptograficzny służący do szyfrowania i odszyfrowywania danych może zawierać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c5da4-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1. <span data-ttu-id="c5da4-105">Każda ze stron generuje parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="c5da4-105">Each party generates a public/private key pair.</span></span>  
  
2. <span data-ttu-id="c5da4-106">Strony wymieniają swoje klucze publiczne.</span><span class="sxs-lookup"><span data-stu-id="c5da4-106">The parties exchange their public keys.</span></span>  
  
3. <span data-ttu-id="c5da4-107">Każda ze stron generuje klucz tajny na potrzeby szyfrowania TripleDES, na przykład i szyfruje nowo utworzony klucz przy użyciu klucza publicznego drugiego.</span><span class="sxs-lookup"><span data-stu-id="c5da4-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4. <span data-ttu-id="c5da4-108">Każda ze stron wysyła dane do drugiej i łączy klucz tajny z własnym, w określonej kolejności, w celu utworzenia nowego klucza tajnego.</span><span class="sxs-lookup"><span data-stu-id="c5da4-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5. <span data-ttu-id="c5da4-109">Następnie strony inicjują konwersację przy użyciu szyfrowania symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="c5da4-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="c5da4-110">Tworzenie schematu kryptograficznego nie jest zadaniem prostym.</span><span class="sxs-lookup"><span data-stu-id="c5da4-110">Creating a cryptographic scheme is not a trivial task.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c5da4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5da4-111">See also</span></span>

- [<span data-ttu-id="c5da4-112">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="c5da4-112">Cryptographic Services</span></span>](cryptographic-services.md)
