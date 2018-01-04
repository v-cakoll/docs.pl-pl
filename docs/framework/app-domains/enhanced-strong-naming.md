---
title: Poprawa silnego nazywania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77eec473b95720e432c94b79778fa518f3ecf1c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="94164-102">Poprawa silnego nazywania</span><span class="sxs-lookup"><span data-stu-id="94164-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="94164-103">Podpis silnej nazwy jest mechanizmem tożsamości w programie .NET Framework do identyfikowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="94164-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="94164-104">Jest zwykle używany do sprawdzania integralności danych są przekazywane z autora (osoby podpisującej) do adresata (weryfikatora) podpis cyfrowy klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="94164-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="94164-105">Ta sygnatura jest używana jako unikatową tożsamość zestawu i zapewnia, że odwołania do zestawu nie są niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="94164-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="94164-106">Zestaw jest podpisany jako część procesu kompilacji, a następnie zweryfikować po załadowaniu go.</span><span class="sxs-lookup"><span data-stu-id="94164-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="94164-107">Podpisy silnej nazwy pomagać w zapobieganiu strony złośliwych przed naruszeniem z zestawem i następnie ponowne podpisanie zestawu z oryginalnego podpisującego klucza.</span><span class="sxs-lookup"><span data-stu-id="94164-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="94164-108">Jednak kluczy silnej nazwy nie mogą zawierać żadnych wiarygodnych informacji o wydawcy ani one zawierać hierarchii certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="94164-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="94164-109">Podpisu silnej nazwy nie gwarantuje wiarygodności osoby podpisującej zestawu lub wskazuje, czy osoba była uzasadnionych właściciela klucza; Wskazuje on tylko, że właściciel klucza podpisana zestawu.</span><span class="sxs-lookup"><span data-stu-id="94164-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="94164-110">Dlatego zaleca się używania podpisu silnej nazwy jako moduł weryfikacji zabezpieczeń dla ufających kodu innych firm.</span><span class="sxs-lookup"><span data-stu-id="94164-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="94164-111">Microsoft Authenticode jest zalecanym sposobem uwierzytelniania kodu.</span><span class="sxs-lookup"><span data-stu-id="94164-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="94164-112">Ograniczenia z konwencjonalnej silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="94164-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="94164-113">Silnych nazw technologii używanej do wersji sprzed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ma następujące niedociągnięć:</span><span class="sxs-lookup"><span data-stu-id="94164-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="94164-114">Klucze są stale zaatakowane i ulepszone technik i sprzętu ułatwiają wnioskować klucz prywatny z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="94164-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="94164-115">Ochrona przed atakami, większe klucze są wymagane.</span><span class="sxs-lookup"><span data-stu-id="94164-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="94164-116">Wersje programu .NET framework, przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zapewniają możliwość podpisać dowolny klawisz rozmiaru (rozmiar domyślny to 1024 bity), ale podpisywanie zestawu przy użyciu nowego klucza dzieli wszystkie pliki binarne, odwołujące się do starszych tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="94164-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="94164-117">W związku z tym jest bardzo trudne do uaktualnienia rozmiar klucza podpisywania, jeśli chcesz zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="94164-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="94164-118">Podpisywanie silną nazwą obsługuje tylko algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="94164-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="94164-119">Ostatnio odnaleziono SHA-1 być nieodpowiednie dla bezpiecznych aplikacji wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="94164-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="94164-120">W związku z tym silniejszego algorytmu (SHA-256 lub nowszego) jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="94164-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="94164-121">Istnieje możliwość, że SHA-1 spowoduje utratę stałego zgodne ze standardem FIPS, które przedstawia problemy dla tych, którzy korzystać tylko algorytmy i oprogramowania zgodne ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="94164-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="94164-122">Zalety rozszerzonych silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="94164-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="94164-123">Główne zalety rozszerzonych silnych nazw są zgodność z istniejącym silne nazwy i możliwości, aby potwierdzić, że jedną tożsamość jest odpowiednikiem innego:</span><span class="sxs-lookup"><span data-stu-id="94164-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="94164-124">Deweloperów, którzy mają istniejące zestawy podpisane można migrować tożsamości do algorytmów SHA-2, zachowując zgodność z zestawy, które odwołują się do starego tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="94164-125">Deweloperzy tworzący nowe zestawy i nie są związane z istniejącym podpisów silnej nazwy za pomocą bardziej bezpieczne algorytmy SHA-2 i zarejestrować zestawy zawsze mają.</span><span class="sxs-lookup"><span data-stu-id="94164-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="94164-126">Przy użyciu rozszerzonych silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="94164-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="94164-127">Kluczy silnej nazwy składają się z klucza podpisu i klucz tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="94164-128">Zestaw jest podpisany przy użyciu klucza podpisu i jest identyfikowany za pomocą klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="94164-129">Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], te dwa klucze były identyczne.</span><span class="sxs-lookup"><span data-stu-id="94164-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="94164-130">Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klucz tożsamości jest taka sama jak w starszych wersjach systemu .NET Framework, ale klucz podpisu jest rozszerzona o silniejszy algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="94164-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="94164-131">Ponadto klucz podpisu jest podpisany przy użyciu klucza tożsamości do tworzenia podpisu zaradczych.</span><span class="sxs-lookup"><span data-stu-id="94164-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="94164-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybut umożliwia metadanych zestawu do istniejącego klucza publicznego na użytek tożsamości zestawu, dzięki czemu stare odwołania do zestawów kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="94164-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="94164-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybut używa zaradczych podpisu do zapewnienia, że właściciel nowego klucza podpisu jest również właściciela starego klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="94164-134">Podpisywanie za pomocą algorytmu SHA-2, bez klucza migracji</span><span class="sxs-lookup"><span data-stu-id="94164-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="94164-135">Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw bez podpisu silnej nazwy migracji:</span><span class="sxs-lookup"><span data-stu-id="94164-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="94164-136">(Jeśli to konieczne), należy wygenerować nowy klucz tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="94164-137">Wyodrębnij klucza publicznego tożsamości, a następnie określ, że algorytm SHA-2 powinny być używane podczas logowania przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="94164-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="94164-138">Opóźnione podpisywanie zestawu z pliku klucza publicznego tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="94164-139">Ponowne podpisanie zestawu z pary kluczy pełnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="94164-140">Podpisywanie za pomocą algorytmu SHA-2, migracja klucza</span><span class="sxs-lookup"><span data-stu-id="94164-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="94164-141">Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw za pomocą podpisu silnej nazwy zmigrowane.</span><span class="sxs-lookup"><span data-stu-id="94164-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="94164-142">Generowanie pary kluczy i podpis (Jeśli to konieczne).</span><span class="sxs-lookup"><span data-stu-id="94164-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="94164-143">Wyodrębnij klucz publiczny podpisu, a następnie określ, że algorytm SHA-2 powinny być używane podczas logowania przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="94164-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="94164-144">Wyodrębnij tożsamości klucza publicznego, który określa algorytm skrótu, który generuje sygnaturę zaradczych.</span><span class="sxs-lookup"><span data-stu-id="94164-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="94164-145">Generowanie parametry <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybutu, a następnie dołącz atrybut do zestawu.</span><span class="sxs-lookup"><span data-stu-id="94164-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  <span data-ttu-id="94164-146">Opóźnione podpisywanie zestawu z kluczem publicznym tożsamości.</span><span class="sxs-lookup"><span data-stu-id="94164-146">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="94164-147">Pełni podpisać zestawu z pary kluczy podpisu.</span><span class="sxs-lookup"><span data-stu-id="94164-147">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="94164-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94164-148">See Also</span></span>  
 [<span data-ttu-id="94164-149">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="94164-149">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
