---
title: Model kryptografii programu .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9fb0a726a4bef5b6efa67d5f63c1899468f7e8ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="3cd2b-102">Model kryptografii programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3cd2b-102">.NET Framework Cryptography Model</span></span>
<span data-ttu-id="3cd2b-103">.NET Framework zapewnia implementacji wiele standardowych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="3cd2b-104">Algorytmy te są łatwe w użyciu i mieć najbezpieczniejszy możliwe domyślnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="3cd2b-105">Ponadto model kryptografii .NET Framework dziedziczenia obiektu, strumienia projektowania i konfiguracji jest bardzo rozszerzonego.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>  
  
## <a name="object-inheritance"></a><span data-ttu-id="3cd2b-106">Obiekt dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="3cd2b-106">Object Inheritance</span></span>  
 <span data-ttu-id="3cd2b-107">System zabezpieczeń .NET Framework implementuje extensible wzorzec dziedziczenia klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="3cd2b-108">Hierarchia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-108">The hierarchy is as follows:</span></span>  
  
-   <span data-ttu-id="3cd2b-109">Typ algorytmu klasy, takich jak <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> lub <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="3cd2b-110">Ten poziom jest abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-110">This level is abstract.</span></span>  
  
-   <span data-ttu-id="3cd2b-111">Klasa algorytmu, który dziedziczy z klasy typu algorytmu; na przykład <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, lub <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="3cd2b-112">Ten poziom jest abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-112">This level is abstract.</span></span>  
  
-   <span data-ttu-id="3cd2b-113">Implementacja klasy algorytmu, który dziedziczy z klasy algorytm; na przykład <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, lub <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="3cd2b-114">Ten poziom pełni jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-114">This level is fully implemented.</span></span>  
  
 <span data-ttu-id="3cd2b-115">Za pomocą tego wzorca klas pochodnych, jest łatwo dodać nowy algorytm lub nowej implementacji istniejących algorytmu.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="3cd2b-116">Na przykład aby utworzyć nowy algorytm klucza publicznego, użytkownik będzie dziedziczyć <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="3cd2b-117">Aby utworzyć nową implementacją określonego algorytmu, należy utworzyć nieabstrakcyjnej klasy pochodnej z tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="3cd2b-118">Jak algorytmy są implementowane w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3cd2b-118">How Algorithms Are Implemented in the .NET Framework</span></span>  
 <span data-ttu-id="3cd2b-119">Na przykład różnych implementacji dostępne dla algorytmu należy wziąć pod uwagę symetryczne algorytmy.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="3cd2b-120">Podstawowa dla wszystkich symetryczne algorytmy jest <xref:System.Security.Cryptography.SymmetricAlgorithm>, który jest dziedziczona przez następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <span data-ttu-id="3cd2b-121"><xref:System.Security.Cryptography.Aes>jest dziedziczona przez dwie klasy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> i <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="3cd2b-122"><xref:System.Security.Cryptography.AesCryptoServiceProvider> Klasy jest otokę implementacji interfejsu API kryptografii systemu Windows (CAPI) Aes, podczas gdy <xref:System.Security.Cryptography.AesManaged> klasy są zapisywane w całości kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="3cd2b-123">Istnieje również trzeci typ implementacji kryptografii nowej generacji (CNG), w implementacji CAPI i dodanie do zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="3cd2b-124">Przykładem jest algorytm CNG jest <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="3cd2b-125">Algorytmy CNG są dostępne w systemie Windows Vista lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-125">CNG algorithms are available on Windows Vista and later.</span></span>  
  
 <span data-ttu-id="3cd2b-126">Można wybrać, którego implementacja jest najlepsze dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="3cd2b-127">Implementacje zarządzane są dostępne na wszystkich platformach, które obsługuje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="3cd2b-128">Implementacje CAPI są dostępne w starszych systemach operacyjnych i są już tworzone.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="3cd2b-129">CNG jest implementacją najnowszych, gdzie nastąpi nowych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="3cd2b-130">Jednak zarządzanych implementacji nie zostały zatwierdzone przez przetwarzanie standardami FIPS (Federal Information) i może być mniejsza niż klasy otoki.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>  
  
## <a name="stream-design"></a><span data-ttu-id="3cd2b-131">Projekt strumienia</span><span class="sxs-lookup"><span data-stu-id="3cd2b-131">Stream Design</span></span>  
 <span data-ttu-id="3cd2b-132">Środowisko uruchomieniowe języka wspólnego używa strumienia zorientowany wykonania symetryczne algorytmy i algorytmów wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="3cd2b-133">Podstawowe ten projekt jest <xref:System.Security.Cryptography.CryptoStream> klasy, która jest pochodną <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="3cd2b-134">Na podstawie strumienia kryptograficznych obiekty obsługują interfejs pojedynczy standardowy (`CryptoStream`) do obsługi części transferu danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="3cd2b-135">Ponieważ wszystkie obiekty są tworzone na standardowy interfejs, użytkownik może łańcuch wielu obiektów (na przykład obiektu skrótu, a następnie za pomocą obiektu szyfrowania) i mogą wykonywać wiele operacji na danych, bez konieczności wszelkie pośrednie magazynu dla niego.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="3cd2b-136">Model przesyłania strumieniowego umożliwia również tworzenie obiektów z mniejszym obiektów.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="3cd2b-137">Na przykład łączna algorytmu szyfrowania i wyznaczania wartości skrótu można wyświetlać jako obiekt jednego strumienia, chociaż ten obiekt może być zbudowane z zestawu obiektów strumienia.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>  
  
## <a name="cryptographic-configuration"></a><span data-ttu-id="3cd2b-138">Konfiguracja usług kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="3cd2b-138">Cryptographic Configuration</span></span>  
 <span data-ttu-id="3cd2b-139">Konfiguracja kryptograficznych pozwala możesz rozwiązać określonej implementacji algorytm nazwę algorytmu, umożliwiając rozszerzalności klasy kryptografii platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="3cd2b-140">Możesz dodać własnego sprzętu lub oprogramowania Implementacja algorytmu i mapowania implementacji nazwę algorytmu wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="3cd2b-141">Jeśli w pliku konfiguracji nie określono algorytmu, używane są ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="3cd2b-142">Aby uzyskać więcej informacji na temat konfiguracji kryptograficznych, zobacz [Konfigurowanie klasy kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="3cd2b-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>  
  
## <a name="choosing-an-algorithm"></a><span data-ttu-id="3cd2b-143">Wybieranie algorytmu</span><span class="sxs-lookup"><span data-stu-id="3cd2b-143">Choosing an Algorithm</span></span>  
 <span data-ttu-id="3cd2b-144">Można wybrać algorytm różnych powodów: na przykład w przypadku integralność danych, poufność danych, lub aby wygenerować klucz.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="3cd2b-145">Algorytmy Symmetric i wyznaczania wartości skrótu są przeznaczone do ochrony danych albo integralności (Ochrona z zmian) lub prywatności przyczyn (Ochrona z wyświetlanie).</span><span class="sxs-lookup"><span data-stu-id="3cd2b-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="3cd2b-146">Algorytmy wyznaczania wartości skrótu są używane głównie w celu zapewnienia integralności danych.</span><span class="sxs-lookup"><span data-stu-id="3cd2b-146">Hash algorithms are used primarily for data integrity.</span></span>  
  
 <span data-ttu-id="3cd2b-147">Poniżej przedstawiono listę zalecanych algorytmów przez aplikację:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-147">Here is a list of recommended algorithms by application:</span></span>  
  
-   <span data-ttu-id="3cd2b-148">Prywatność danych:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-148">Data privacy:</span></span>  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   <span data-ttu-id="3cd2b-149">Integralność danych:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-149">Data integrity:</span></span>  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   <span data-ttu-id="3cd2b-150">Podpis cyfrowy:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-150">Digital signature:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="3cd2b-151">Wymiana kluczy:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-151">Key exchange:</span></span>  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   <span data-ttu-id="3cd2b-152">Generowanie liczby losowej:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-152">Random number generation:</span></span>  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   <span data-ttu-id="3cd2b-153">Generowanie klucza z hasła:</span><span class="sxs-lookup"><span data-stu-id="3cd2b-153">Generating a key from a password:</span></span>  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a><span data-ttu-id="3cd2b-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cd2b-154">See Also</span></span>  
 [<span data-ttu-id="3cd2b-155">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="3cd2b-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 
