---
title: Model kryptografii programu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42e5c7018f83f3849f46f33e09e09ea1749e7c70
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753285"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="9645d-102">Model kryptografii programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9645d-102">.NET Framework Cryptography Model</span></span>

<span data-ttu-id="9645d-103">.NET Framework zawiera implementacje wiele standardowych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="9645d-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="9645d-104">Algorytmy te są łatwe w użyciu i ma najbezpieczniejszą możliwe domyślne właściwości.</span><span class="sxs-lookup"><span data-stu-id="9645d-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="9645d-105">Ponadto model kryptografii .NET Framework, dziedziczenie obiektu, projekt usługi stream i konfiguracji jest bardzo rozszerzalny.</span><span class="sxs-lookup"><span data-stu-id="9645d-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="9645d-106">Dziedziczenie obiektu</span><span class="sxs-lookup"><span data-stu-id="9645d-106">Object Inheritance</span></span>

<span data-ttu-id="9645d-107">System zabezpieczeń .NET Framework implementuje extensible wzorzec dziedziczenia klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="9645d-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="9645d-108">Hierarchia jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9645d-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="9645d-109">Typ algorytmu klasy takie jak <xref:System.Security.Cryptography.SymmetricAlgorithm>, <xref:System.Security.Cryptography.AsymmetricAlgorithm> lub <xref:System.Security.Cryptography.HashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="9645d-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="9645d-110">Ten poziom jest abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="9645d-110">This level is abstract.</span></span>

- <span data-ttu-id="9645d-111">Klasa algorytmu, który dziedziczy z klasy typu algorytmu; na przykład <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, lub <xref:System.Security.Cryptography.ECDiffieHellman>.</span><span class="sxs-lookup"><span data-stu-id="9645d-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="9645d-112">Ten poziom jest abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="9645d-112">This level is abstract.</span></span>

- <span data-ttu-id="9645d-113">Implementacja klasy algorytmu, który dziedziczy z klasy algorytm; na przykład <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, lub <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="9645d-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="9645d-114">Ten poziom jest w pełni zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="9645d-114">This level is fully implemented.</span></span>

<span data-ttu-id="9645d-115">Za pomocą tego wzorca klasy pochodne, jest łatwe do dodania, nowy algorytm lub nową metodę implementacji algorytm istniejących.</span><span class="sxs-lookup"><span data-stu-id="9645d-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="9645d-116">Na przykład, aby utworzyć nowy algorytm klucza publicznego, użytkownik będzie dziedziczyć <xref:System.Security.Cryptography.AsymmetricAlgorithm> klasy.</span><span class="sxs-lookup"><span data-stu-id="9645d-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="9645d-117">Aby utworzyć nową metodę implementacji określonego algorytmu, należy utworzyć klasę pochodną nieabstrakcyjnej tego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="9645d-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="9645d-118">Jak algorytmy są implementowane w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9645d-118">How Algorithms Are Implemented in the .NET Framework</span></span>

<span data-ttu-id="9645d-119">Jako przykład różne implementacje dostępne dla algorytmu należy wziąć pod uwagę algorytmów symetrycznych.</span><span class="sxs-lookup"><span data-stu-id="9645d-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="9645d-120">Podstawa dla wszystkich algorytmów symetrycznych jest <xref:System.Security.Cryptography.SymmetricAlgorithm>, która jest dziedziczona przez następujących algorytmów:</span><span class="sxs-lookup"><span data-stu-id="9645d-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>

1. <xref:System.Security.Cryptography.Aes>

2. <xref:System.Security.Cryptography.DES>

3. <xref:System.Security.Cryptography.RC2>

4. <xref:System.Security.Cryptography.Rijndael>

5. <xref:System.Security.Cryptography.TripleDES>

<span data-ttu-id="9645d-121"><xref:System.Security.Cryptography.Aes> jest dziedziczona przez dwie klasy: <xref:System.Security.Cryptography.AesCryptoServiceProvider> i <xref:System.Security.Cryptography.AesManaged>.</span><span class="sxs-lookup"><span data-stu-id="9645d-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="9645d-122"><xref:System.Security.Cryptography.AesCryptoServiceProvider> Klasy jest otokę wdrożenia Windows Cryptography API (CAPI) Aes, podczas gdy <xref:System.Security.Cryptography.AesManaged> klasy jest napisanych w całości w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="9645d-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="9645d-123">Istnieje również trzeci typ implementacji Cryptography Next Generation (CNG), w dodatku do zarządzanych i CAPI implementacji.</span><span class="sxs-lookup"><span data-stu-id="9645d-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="9645d-124">Na przykład algorytm CNG <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span><span class="sxs-lookup"><span data-stu-id="9645d-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="9645d-125">Algorytmy CNG są dostępne w systemie Windows Vista i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="9645d-125">CNG algorithms are available on Windows Vista and later.</span></span>

<span data-ttu-id="9645d-126">Możesz wybrać, która implementacja jest odpowiedni dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="9645d-126">You can choose which implementation is best for you.</span></span>  <span data-ttu-id="9645d-127">Implementacje zarządzane są dostępne na wszystkich platformach, które obsługują .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9645d-127">The managed implementations are available on all platforms that support the .NET Framework.</span></span>  <span data-ttu-id="9645d-128">Implementacje CAPI są dostępne w starszych systemach operacyjnych, a nie są już opracowywane są.</span><span class="sxs-lookup"><span data-stu-id="9645d-128">The CAPI implementations are available on older operating systems, and are no longer being developed.</span></span> <span data-ttu-id="9645d-129">CNG jest implementacją najnowsze, w której nowych wdrożeń będzie miała miejsce.</span><span class="sxs-lookup"><span data-stu-id="9645d-129">CNG is the very latest implementation where new development will take place.</span></span> <span data-ttu-id="9645d-130">Jednak implementacji zarządzanej nie zostały zatwierdzone przez przetwarzanie standardów FIPS (Federal Information) i może być wolniejsze niż klasy otoki.</span><span class="sxs-lookup"><span data-stu-id="9645d-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>

## <a name="stream-design"></a><span data-ttu-id="9645d-131">Stream projektu</span><span class="sxs-lookup"><span data-stu-id="9645d-131">Stream Design</span></span>

<span data-ttu-id="9645d-132">Środowisko uruchomieniowe języka wspólnego używa projektu zorientowane na strumień wykonania symetryczne algorytmy i algorytmów wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="9645d-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="9645d-133">Podstawowe ten projekt jest <xref:System.Security.Cryptography.CryptoStream> klasy, która jest pochodną <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="9645d-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="9645d-134">Na podstawie Stream obiekty usług kryptograficznych obsługują interfejs jednego standardowego (`CryptoStream`) do obsługi transferu danych część obiektu.</span><span class="sxs-lookup"><span data-stu-id="9645d-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="9645d-135">Ponieważ wszystkie obiekty są oparte na standardowych interfejsów, można połączyć w łańcuch jednocześnie wielu obiektów (takich jak obiektu skrótu, a następnie za pomocą obiektu szyfrowanie) i wykonywać wiele operacji na danych bez konieczności używania magazynu pośredniego dla niego.</span><span class="sxs-lookup"><span data-stu-id="9645d-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="9645d-136">Modelu przesyłania strumieniowego umożliwia również tworzenie obiektów z mniejszych obiektów.</span><span class="sxs-lookup"><span data-stu-id="9645d-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="9645d-137">Na przykład połączone algorytm szyfrowania i wyznaczania wartości skrótu można wyświetlać jako obiekt jednemu strumieniowi, chociaż ten obiekt może być kompilowany z zestawu obiektów strumienia.</span><span class="sxs-lookup"><span data-stu-id="9645d-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>

## <a name="cryptographic-configuration"></a><span data-ttu-id="9645d-138">Konfiguracji kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="9645d-138">Cryptographic Configuration</span></span>

<span data-ttu-id="9645d-139">Konfiguracji kryptograficznej pozwala rozpoznać określoną implementację algorytmu Nazwa algorytmu, umożliwiając rozszerzania klasy kryptografii platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9645d-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="9645d-140">Można dodać Twojej własnej implementacji sprzętowego lub programowego algorytmu i mapowania implementacja na Nazwa algorytmu wybranych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9645d-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="9645d-141">Jeśli nie określono algorytmu w pliku konfiguracji, ustawienia domyślne są używane.</span><span class="sxs-lookup"><span data-stu-id="9645d-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="9645d-142">Aby uzyskać więcej informacji na temat konfiguracji kryptograficznej zobacz [konfigurowanie klas kryptografii](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9645d-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../../docs/framework/configure-apps/configure-cryptography-classes.md).</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="9645d-143">Wybieranie algorytmu</span><span class="sxs-lookup"><span data-stu-id="9645d-143">Choosing an Algorithm</span></span>

<span data-ttu-id="9645d-144">Możesz wybrać algorytm różnych powodów: na przykład integralność danych, ochrony prywatności danych lub do generowania klucza.</span><span class="sxs-lookup"><span data-stu-id="9645d-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="9645d-145">Algorytmy Symmetric i wyznaczania wartości skrótu są przeznaczone do ochrony danych dla albo integralności (Ochrona zmiana) lub zachowania przyczyn (Ochrona z przeglądania).</span><span class="sxs-lookup"><span data-stu-id="9645d-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="9645d-146">Algorytmy wyznaczania wartości skrótu są używane przede wszystkim dotyczące integralności danych.</span><span class="sxs-lookup"><span data-stu-id="9645d-146">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="9645d-147">Poniżej przedstawiono listę zalecanych algorytmów przez aplikację:</span><span class="sxs-lookup"><span data-stu-id="9645d-147">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="9645d-148">Prywatność danych:</span><span class="sxs-lookup"><span data-stu-id="9645d-148">Data privacy:</span></span>

  - <xref:System.Security.Cryptography.Aes>

- <span data-ttu-id="9645d-149">Integralność danych:</span><span class="sxs-lookup"><span data-stu-id="9645d-149">Data integrity:</span></span>

  - <xref:System.Security.Cryptography.HMACSHA256>

  - <xref:System.Security.Cryptography.HMACSHA512>

- <span data-ttu-id="9645d-150">Podpis cyfrowy:</span><span class="sxs-lookup"><span data-stu-id="9645d-150">Digital signature:</span></span>

  - <xref:System.Security.Cryptography.ECDsa>

  - <xref:System.Security.Cryptography.RSA>

- <span data-ttu-id="9645d-151">Wymiana klucza:</span><span class="sxs-lookup"><span data-stu-id="9645d-151">Key exchange:</span></span>

  - <xref:System.Security.Cryptography.ECDiffieHellman>

  - <xref:System.Security.Cryptography.RSA>

- <span data-ttu-id="9645d-152">Generowanie liczby losowej:</span><span class="sxs-lookup"><span data-stu-id="9645d-152">Random number generation:</span></span>

  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>

- <span data-ttu-id="9645d-153">Generowanie klucza hasła:</span><span class="sxs-lookup"><span data-stu-id="9645d-153">Generating a key from a password:</span></span>

  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="9645d-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9645d-154">See also</span></span>

- [<span data-ttu-id="9645d-155">Usługi kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="9645d-155">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
