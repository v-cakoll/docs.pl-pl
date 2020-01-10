---
title: 'Porady: dostęp do sprzętowych urządzeń szyfrujących'
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
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706178"
---
# <a name="how-to-access-hardware-encryption-devices"></a><span data-ttu-id="969dd-102">Porady: dostęp do sprzętowych urządzeń szyfrujących</span><span class="sxs-lookup"><span data-stu-id="969dd-102">How to: Access Hardware Encryption Devices</span></span>
<span data-ttu-id="969dd-103">Aby uzyskać dostęp do urządzeń do szyfrowania sprzętu, można użyć klasy <xref:System.Security.Cryptography.CspParameters>.</span><span class="sxs-lookup"><span data-stu-id="969dd-103">You can use the <xref:System.Security.Cryptography.CspParameters> class to access hardware encryption devices.</span></span> <span data-ttu-id="969dd-104">Na przykład można użyć tej klasy do zintegrowania aplikacji z kartą inteligentną, generatorem losowych liczb sprzętowych lub sprzętową implementacją określonego algorytmu kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="969dd-104">For example, you can use this class to integrate your application with a smart card, a hardware random number generator, or a hardware implementation of a particular cryptographic algorithm.</span></span>  
  
 <span data-ttu-id="969dd-105">Klasa <xref:System.Security.Cryptography.CspParameters> tworzy dostawcę usług kryptograficznych (CSP), który uzyskuje dostęp do prawidłowo zainstalowanego urządzenia szyfrującego sprzętowego.</span><span class="sxs-lookup"><span data-stu-id="969dd-105">The <xref:System.Security.Cryptography.CspParameters> class creates a cryptographic service provider (CSP) that accesses a properly installed hardware encryption device.</span></span>  <span data-ttu-id="969dd-106">Dostępność dostawcy CSP można sprawdzić, sprawdzając następujący klucz rejestru przy użyciu Edytora rejestru (regedit. exe): HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.</span><span class="sxs-lookup"><span data-stu-id="969dd-106">You can verify the availability of a CSP by inspecting the following registry key using the Registry Editor (Regedit.exe):  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.</span></span>  
  
### <a name="to-sign-data-using-a-key-card"></a><span data-ttu-id="969dd-107">Aby podpisać dane przy użyciu karty klucza</span><span class="sxs-lookup"><span data-stu-id="969dd-107">To sign data using a key card</span></span>  
  
1. <span data-ttu-id="969dd-108">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters>, przekazując typ dostawcy integer i nazwę dostawcy do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="969dd-108">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="969dd-109">Przekaż odpowiednie flagi do właściwości <xref:System.Security.Cryptography.CspParameters.Flags%2A> nowo utworzonego obiektu <xref:System.Security.Cryptography.CspParameters>.</span><span class="sxs-lookup"><span data-stu-id="969dd-109">Pass the appropriate flags to the <xref:System.Security.Cryptography.CspParameters.Flags%2A> property of the newly created <xref:System.Security.Cryptography.CspParameters> object.</span></span>  <span data-ttu-id="969dd-110">Na przykład Przekaż flagę <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.</span><span class="sxs-lookup"><span data-stu-id="969dd-110">For example, pass the <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> flag.</span></span>  
  
3. <span data-ttu-id="969dd-111">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.AsymmetricAlgorithm> (na przykład klasy <xref:System.Security.Cryptography.RSACryptoServiceProvider>), przekazując obiekt <xref:System.Security.Cryptography.CspParameters> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="969dd-111">Create a new instance of an <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (for example, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class), passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
4. <span data-ttu-id="969dd-112">Podpisz swoje dane przy użyciu jednej z `Sign` metod i sprawdź swoje dane przy użyciu jednej z metod `Verify`.</span><span class="sxs-lookup"><span data-stu-id="969dd-112">Sign your data using one of the `Sign` methods and verify your data using one of the `Verify` methods.</span></span>  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a><span data-ttu-id="969dd-113">Aby wygenerować liczbę losową przy użyciu generatora liczb losowych sprzętowych</span><span class="sxs-lookup"><span data-stu-id="969dd-113">To generate a random number using a hardware random number generator</span></span>  
  
1. <span data-ttu-id="969dd-114">Utwórz nowe wystąpienie klasy <xref:System.Security.Cryptography.CspParameters>, przekazując typ dostawcy integer i nazwę dostawcy do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="969dd-114">Create a new instance of the <xref:System.Security.Cryptography.CspParameters> class, passing the integer provider type and the provider name to the constructor.</span></span>  
  
2. <span data-ttu-id="969dd-115">Utwórz nowe wystąpienie <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, przekazując obiekt <xref:System.Security.Cryptography.CspParameters> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="969dd-115">Create a new instance of the <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passing the <xref:System.Security.Cryptography.CspParameters> object to the constructor.</span></span>  
  
3. <span data-ttu-id="969dd-116">Utwórz wartość losową przy użyciu metody <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> lub <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.</span><span class="sxs-lookup"><span data-stu-id="969dd-116">Create a random value using the <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> or <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="969dd-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="969dd-117">Example</span></span>  
 <span data-ttu-id="969dd-118">Poniższy przykład kodu demonstruje sposób podpisywania danych przy użyciu karty inteligentnej.</span><span class="sxs-lookup"><span data-stu-id="969dd-118">The following code example demonstrates how to sign data using a smart card.</span></span>  <span data-ttu-id="969dd-119">Przykładowy kod tworzy obiekt <xref:System.Security.Cryptography.CspParameters>, który uwidacznia kartę inteligentną, a następnie inicjuje obiekt <xref:System.Security.Cryptography.RSACryptoServiceProvider> przy użyciu dostawcy CSP.</span><span class="sxs-lookup"><span data-stu-id="969dd-119">The code example creates a <xref:System.Security.Cryptography.CspParameters> object that exposes a smart card, and then initializes an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object using the CSP.</span></span>  <span data-ttu-id="969dd-120">Przykład kodu następnie podpisuje i weryfikuje niektóre dane.</span><span class="sxs-lookup"><span data-stu-id="969dd-120">The code example then signs and verifies some data.</span></span>  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="969dd-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="969dd-121">Compiling the Code</span></span>  
  
- <span data-ttu-id="969dd-122">Uwzględnij <xref:System> i <xref:System.Security.Cryptography> przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="969dd-122">Include the <xref:System> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
- <span data-ttu-id="969dd-123">Na komputerze musi być zainstalowany czytnik kart inteligentnych i sterowniki.</span><span class="sxs-lookup"><span data-stu-id="969dd-123">You must have a smart card reader and drivers installed on your computer.</span></span>  
  
- <span data-ttu-id="969dd-124">Należy zainicjować obiekt <xref:System.Security.Cryptography.CspParameters> przy użyciu informacji specyficznych dla czytnika kart.</span><span class="sxs-lookup"><span data-stu-id="969dd-124">You must initialize the <xref:System.Security.Cryptography.CspParameters> object using information specific to your card reader.</span></span>  <span data-ttu-id="969dd-125">Aby uzyskać więcej informacji, zobacz dokumentację czytnika kart.</span><span class="sxs-lookup"><span data-stu-id="969dd-125">For more information, see the documentation of your card reader.</span></span>
