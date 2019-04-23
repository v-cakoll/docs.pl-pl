---
title: 'Instrukcje: Dostęp do sprzętowych urządzeń szyfrujących'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33af618ac3971df76683fd64346e1aa1e5977177
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773418"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="25be7-102">Instrukcje: Dostęp do sprzętowych urządzeń szyfrujących</span><span class="sxs-lookup"><span data-stu-id="25be7-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="25be7-103">Możesz użyć <xref:System.Security.Cryptography.CspParameters> klasy, aby dostęp do sprzętowych urządzeń szyfrujących.</span><span class="sxs-lookup"><span data-stu-id="25be7-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="25be7-104">Na przykład można użyć tej klasy można zintegrować aplikację z karty inteligentnej, sprzęt generator liczb losowych lub z implementacją sprzętu określonego algorytmu kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="25be7-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="25be7-105"><xref:System.Security.Cryptography.CspParameters> Klasy tworzy dostawcy usług kryptograficznych (CSP), który uzyskuje dostęp do urządzenia szyfrowania sprzętowego poprawnie zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="25be7-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="25be7-106">Możesz sprawdzić dostępność dostawcy usług Kryptograficznych, sprawdzając następujący klucz rejestru za pomocą Edytora rejestru (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="25be7-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="25be7-107">Aby zarejestrować dane przy użyciu karta klucza</span><span class="sxs-lookup"><span data-stu-id="25be7-107">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="25be7-108">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> klasy, przekazując całkowitą typ dostawcy i nazwy dostawcy do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="25be7-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="25be7-109">Przekaż odpowiednie flagi, aby <xref:System.Security.Cryptography.CspParameters.Flags%2A> właściwości nowo utworzonej <xref:System.Security.Cryptography.CspParameters> obiektu.</span><span class="sxs-lookup"><span data-stu-id="25be7-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="25be7-110">Na przykład przekazać <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flagi.</span><span class="sxs-lookup"><span data-stu-id="25be7-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="25be7-111">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy (na przykład <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy), przekazując <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="25be7-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="25be7-112">Zaloguj się do danych przy użyciu jednej z `Sign` metod i sprawdź swoje dane przy użyciu jednej z `Verify` metody.</span><span class="sxs-lookup"><span data-stu-id="25be7-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="25be7-113">Aby wygenerować losową liczbę za pomocą sprzętu generator liczb losowych</span><span class="sxs-lookup"><span data-stu-id="25be7-113">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="25be7-114">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters> klasy, przekazując całkowitą typ dostawcy i nazwy dostawcy do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="25be7-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="25be7-115">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, przekazując <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="25be7-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="25be7-116">Tworzenie przy użyciu wartości losowej <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> lub <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="25be7-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25be7-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="25be7-117">Example</span></span>  
 <span data-ttu-id="25be7-118">Poniższy przykład kodu demonstruje sposób rejestrowania danych przy użyciu karty inteligentnej.</span><span class="sxs-lookup"><span data-stu-id="25be7-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="25be7-119">Przykład kodu tworzy <xref:System.Security.Cryptography.CspParameters> obiekt, który udostępnia kart inteligentnych, a następnie inicjuje <xref:System.Security.Cryptography.RSACryptoServiceProvider> przy użyciu dostawcy usług Kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="25be7-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="25be7-120">W przykładzie kodu, a następnie podpisuje i weryfikuje niektórych danych.</span><span class="sxs-lookup"><span data-stu-id="25be7-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25be7-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="25be7-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="25be7-122">Obejmują <xref:System> i <xref:System.Security.Cryptography> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="25be7-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
-   <span data-ttu-id="25be7-123">Konieczne jest posiadanie czytnik kart inteligentnych i sterowniki zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="25be7-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
-   <span data-ttu-id="25be7-124">Należy zainicjować <xref:System.Security.Cryptography.CspParameters> przy użyciu informacji specyficznych dla czytnika kart.</span><span class="sxs-lookup"><span data-stu-id="25be7-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="25be7-125">Więcej informacji na ten temat można znaleźć w dokumentacji czytnika kart.</span><span class="sxs-lookup"><span data-stu-id="25be7-125">For more information, see the documentation of your card reader.</span></span>
