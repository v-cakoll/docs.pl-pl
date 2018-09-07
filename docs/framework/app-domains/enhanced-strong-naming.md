---
title: Poprawa silnego nazywania
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 659f9ffa8ebb10b34300167e9183f60568279513
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44082073"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="2d710-102">Poprawa silnego nazywania</span><span class="sxs-lookup"><span data-stu-id="2d710-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="2d710-103">Podpis silnej nazwy to mechanizm tożsamości w programie .NET Framework do identyfikowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="2d710-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="2d710-104">Jest podpis cyfrowy klucz publiczny, który jest zazwyczaj używany do sprawdzenia integralności danych przekazywanych od inicjatora (osoby podpisującej) do adresata (weryfikatora).</span><span class="sxs-lookup"><span data-stu-id="2d710-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="2d710-105">Ta sygnatura jest używana jako unikatowa tożsamość dla zestawu i zapewnia, że odwołania do zestawu są jednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="2d710-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="2d710-106">Zestaw jest podpisywany jako część procesu kompilacji, a następnie weryfikowany po jego załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="2d710-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="2d710-107">Podpisy silnej nazwy pozwalają zapobiec naruszeniu zestawu, a następnie ponownemu podpisywaniu zestawu za pomocą oryginalnego podpisującego klucza.</span><span class="sxs-lookup"><span data-stu-id="2d710-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="2d710-108">Jednakże klucze o silnych nazwach nie zawierają żadnych wiarygodnych informacji o wydawcy ani zawierają hierarchii certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2d710-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="2d710-109">Podpis silnej nazwy nie gwarantuje wiarygodności osoby, która podpisała zestaw ani nie wskazują, czy osoba była jest prawowitych właścicielem klucza; wskazuje tylko, że właściciela klucza podpisała zestaw.</span><span class="sxs-lookup"><span data-stu-id="2d710-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="2d710-110">W związku z tym nie zalecamy używania podpisu silnej nazwy jako modułu sprawdzania zabezpieczeń dla ufającej kodu innych firm.</span><span class="sxs-lookup"><span data-stu-id="2d710-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="2d710-111">Authenticode firmy Microsoft jest zalecanym sposobem uwierzytelniania kodu.</span><span class="sxs-lookup"><span data-stu-id="2d710-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="2d710-112">Ograniczenia konwencjonalnych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="2d710-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="2d710-113">Technologia silnego nazewnictwa wykorzystywana w wersjach przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ma następujące braki:</span><span class="sxs-lookup"><span data-stu-id="2d710-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="2d710-114">Klucze są stale atakowane i techniki i sprzęt ułatwiają wywnioskować klucza prywatnego z klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="2d710-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="2d710-115">Aby zabezpieczyć się przed atakami, kluczy są niezbędne.</span><span class="sxs-lookup"><span data-stu-id="2d710-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="2d710-116">Wersje programu .NET framework przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zapewniają możliwość podpisywania z dowolnym rozmiarem klucza (rozmiar domyślny wynosi 1024 bity), ale podpisywanie zestawu z nowym kluczem przerywa wszystkie pliki binarne, które odwołują się do starszych tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="2d710-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="2d710-117">W związku z tym, bardzo trudno jest uaktualnianie rozmiaru klucza podpisywania, jeśli chcesz zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="2d710-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="2d710-118">Podpis silnej nazwy obsługuje tylko algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="2d710-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="2d710-119">Ostatnio odnaleziono SHA-1 jako niewystarczający dla bezpiecznych aplikacji mieszania.</span><span class="sxs-lookup"><span data-stu-id="2d710-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="2d710-120">Dlatego jest mocniejszy algorytm (SHA-256 lub większy) jest niezbędne.</span><span class="sxs-lookup"><span data-stu-id="2d710-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="2d710-121">Istnieje możliwość, że algorytm SHA-1 spowoduje utratę stałego zgodne ze standardem FIPS, co przedstawiałoby problemy dla tych, którzy wolą używać tylko zgodne ze standardem FIPS oprogramowanie i algorytmów.</span><span class="sxs-lookup"><span data-stu-id="2d710-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="2d710-122">Zalety rozszerzonych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="2d710-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="2d710-123">Głównymi zaletami rozszerzonych silnych nazw są zgodność z istniejącym silnymi nazwami i możliwość stwierdzenia, że jedna tożsamość jest równoważna z inną:</span><span class="sxs-lookup"><span data-stu-id="2d710-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="2d710-124">Deweloperzy, którzy mają istniejące zestawy podpisane, mogą migrować swoją tożsamość do algorytmów SHA-2 przy zachowaniu zgodności z zestawy odwołujące się do starych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2d710-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="2d710-125">Deweloperzy, którzy tworzą nowe zestawy i nie są związani z istniejącym podpisem silnej nazwy można użyć bardziej bezpieczne algorytmów SHA-2 i podpisywać zestawy tak jak dotychczas.</span><span class="sxs-lookup"><span data-stu-id="2d710-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="2d710-126">Używanie rozszerzonych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="2d710-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="2d710-127">Klucze silnej nazwy składają się z klucza podpisu i klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2d710-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="2d710-128">Zestaw jest podpisany za pomocą klucza podpisu i jest identyfikowany przez klucz tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2d710-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="2d710-129">Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], te dwa klucze były identyczne.</span><span class="sxs-lookup"><span data-stu-id="2d710-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="2d710-130">Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klucz tożsamości pozostaje taki sam jak w starszych wersjach .NET Framework, ale klucz podpisu jest rozszerzony o mocniejszy algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2d710-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="2d710-131">Ponadto klucz podpisu jest podpisany przy użyciu klucza tożsamości do utworzenia kontrsygnatury.</span><span class="sxs-lookup"><span data-stu-id="2d710-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="2d710-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybut pozwala metadanym zestawu do istniejącego klucza publicznego na użytek tożsamość zestawu, co pozwala starym odwołaniom do zestawu na kontynuowanie pracy.</span><span class="sxs-lookup"><span data-stu-id="2d710-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="2d710-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybutu używa kontrsygnatury do zapewnienia, że właściciel nowego klucza podpisu jest również właścicielem starego klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2d710-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="2d710-134">Podpisywanie za pomocą algorytmu SHA-2, bez migracji kluczy</span><span class="sxs-lookup"><span data-stu-id="2d710-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="2d710-135">Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw bez przenoszenia podpisu silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="2d710-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="2d710-136">(Jeśli jest to konieczne), należy wygenerować nowy klucz tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2d710-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="2d710-137">Wyodrębnij klucz publiczny tożsamości, a następnie określić, że algorytm SHA-2 powinien używane podczas logowania przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="2d710-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="2d710-138">Opóźnij podpisanie zestawu z tożsamością pliku klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="2d710-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="2d710-139">Ponowne Podpisz zestaw parą kluczy pełnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="2d710-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="2d710-140">Podpisywanie za pomocą algorytmu SHA-2, z migracją kluczy</span><span class="sxs-lookup"><span data-stu-id="2d710-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="2d710-141">Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw przy użyciu przeniesionego podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d710-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="2d710-142">Generowanie pary kluczy tożsamości i podpisu (jeśli jest to konieczne).</span><span class="sxs-lookup"><span data-stu-id="2d710-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="2d710-143">Wyodrębnij klucz publiczny podpisu i określić, że algorytm SHA-2 powinien używane podczas logowania przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="2d710-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="2d710-144">Wyodrębnij klucz publiczny tożsamości, który określa algorytm wyznaczania wartości skrótu, który generuje kontrsygnaturę.</span><span class="sxs-lookup"><span data-stu-id="2d710-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="2d710-145">Wygeneruj parametry <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybutu i Dołącz atrybut do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2d710-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="2d710-146">To generuje dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="2d710-146">This produces output similar to the following.</span></span>

    ```
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="2d710-147">To danych wyjściowych może następnie zostać przekształcone na AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="2d710-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5.  <span data-ttu-id="2d710-148">Opóźnij podpisanie zestawu z tożsamością klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="2d710-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="2d710-149">W pełni Podpisz zestaw za pomocą pary kluczy podpisu.</span><span class="sxs-lookup"><span data-stu-id="2d710-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d710-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d710-150">See Also</span></span>  
 [<span data-ttu-id="2d710-151">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="2d710-151">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
