---
title: Poprawa silnego nazywania
description: Konwencjonalne sygnatury silnej nazwy dla zestawów w .NET Framework mają ograniczenia. Dowiedz się więcej o ulepszonym silnym nazewnictwie.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 720eda86ef0555127da422b2f44a414e8bbfb1b7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378951"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="70ed7-104">Poprawa silnego nazywania</span><span class="sxs-lookup"><span data-stu-id="70ed7-104">Enhanced strong naming</span></span>
<span data-ttu-id="70ed7-105">Sygnatura silnej nazwy jest mechanizmem tożsamości w .NET Framework do identyfikowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="70ed7-105">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="70ed7-106">Jest to podpis cyfrowy klucza publicznego, który zwykle jest używany do weryfikacji integralności danych, które są przesyłane z nadawcy (osoby podpisującej) do adresata (weryfikatora).</span><span class="sxs-lookup"><span data-stu-id="70ed7-106">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="70ed7-107">Ta sygnatura jest używana jako unikatowa tożsamość zestawu i zapewnia, że odwołania do zestawu nie są niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="70ed7-107">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="70ed7-108">Zestaw jest podpisany jako część procesu kompilacji, a następnie weryfikowany po jego załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-108">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="70ed7-109">Podpisy silnej nazwy uniemożliwiają złośliwym stronom manipulowanie zestawem, a następnie ponowne podpisywanie zestawu przy użyciu oryginalnego klucza osoby podpisującej.</span><span class="sxs-lookup"><span data-stu-id="70ed7-109">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="70ed7-110">Jednak klucze o silnych nazwach nie zawierają żadnych wiarygodnych informacji o wydawcy ani nie zawierają hierarchii certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="70ed7-110">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="70ed7-111">Podpis silnej nazwy nie gwarantuje wiarygodności osoby, która podpisała zestaw lub wskazuje, czy osoba była uprawnionym właścicielem klucza; wskazuje tylko, że właściciel klucza podpisuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="70ed7-111">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="70ed7-112">W związku z tym nie zaleca się używania podpisu silnej nazwy jako modułu sprawdzania zabezpieczeń w celu zaufania kodu innej firmy.</span><span class="sxs-lookup"><span data-stu-id="70ed7-112">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="70ed7-113">Microsoft Authenticode jest zalecanym sposobem uwierzytelniania kodu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-113">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="70ed7-114">Ograniczenia konwencjonalnych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="70ed7-114">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="70ed7-115">Technologia silnego nazewnictwa używana w wersjach przed .NET Framework 4,5 ma następujące braki:</span><span class="sxs-lookup"><span data-stu-id="70ed7-115">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="70ed7-116">Klucze są stale objęte atakami, a udoskonalone techniki i sprzęt ułatwiają wywnioskowanie klucza prywatnego z klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="70ed7-116">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="70ed7-117">Aby chronić przed atakami, potrzebne są większe klucze.</span><span class="sxs-lookup"><span data-stu-id="70ed7-117">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="70ed7-118">Wersje .NET Framework przed .NET Framework 4,5 zapewniają możliwość podpisania przy użyciu dowolnego klucza rozmiaru (domyślny rozmiar to 1024 bitów), ale podpisywanie zestawu z nowym kluczem spowoduje przerwanie wszystkich plików binarnych, które odwołują się do starszej tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-118">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="70ed7-119">W związku z tym jest niezwykle trudne do uaktualnienia rozmiaru klucza podpisywania, jeśli chcesz zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="70ed7-119">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="70ed7-120">Podpisywanie silnej nazwy obsługuje tylko algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="70ed7-120">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="70ed7-121">Wcześniej stwierdzono, że algorytm SHA-1 jest nieodpowiedni dla bezpiecznych aplikacji do tworzenia skrótów.</span><span class="sxs-lookup"><span data-stu-id="70ed7-121">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="70ed7-122">W związku z tym konieczny jest silniejszy algorytm (SHA-256 lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="70ed7-122">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="70ed7-123">Istnieje możliwość, że algorytm SHA-1 utraci swoją pozycję zgodną ze standardem FIPS, co może spowodować problemy dla tych, którzy zdecydują się używać tylko oprogramowania zgodnego ze standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="70ed7-123">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="70ed7-124">Zalety ulepszonych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="70ed7-124">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="70ed7-125">Główne zalety ulepszonych silnych nazw są zgodne ze wstępnie istniejącymi silnymi nazwami i możliwość stwierdzenia, że jedna tożsamość jest równoważna z inną:</span><span class="sxs-lookup"><span data-stu-id="70ed7-125">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="70ed7-126">Deweloperzy, którzy posiadają istniejące podpisane zestawy, mogą migrować swoje tożsamości do algorytmów SHA-2 przy zachowaniu zgodności z zestawami, które odwołują się do starych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-126">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="70ed7-127">Deweloperzy, którzy tworzą nowe zestawy i nie są zainteresowani istniejącymi sygnaturami silnej nazwy, mogą korzystać z bezpieczniejszych algorytmów SHA-2 i podpisywać zestawy w taki sam sposób, jak zawsze.</span><span class="sxs-lookup"><span data-stu-id="70ed7-127">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="70ed7-128">Użyj ulepszonych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="70ed7-128">Use enhanced strong names</span></span>  
 <span data-ttu-id="70ed7-129">Klucze silnej nazwy składają się z klucza podpisu i klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-129">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="70ed7-130">Zestaw jest podpisany przy użyciu klucza podpisu i jest identyfikowany przez klucz tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-130">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="70ed7-131">Przed .NET Framework 4,5 te dwa klucze były takie same.</span><span class="sxs-lookup"><span data-stu-id="70ed7-131">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="70ed7-132">Począwszy od .NET Framework 4,5, klucz tożsamości pozostaje taki sam jak w starszych wersjach .NET Framework, ale klucz podpisu zostanie rozszerzony przy użyciu silniejszego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-132">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="70ed7-133">Ponadto klucz podpisu jest podpisany przy użyciu klucza tożsamości w celu utworzenia podpisu licznika.</span><span class="sxs-lookup"><span data-stu-id="70ed7-133">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="70ed7-134">Ten <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybut umożliwia metadanych zestawu użycie istniejącego klucza publicznego dla tożsamości zestawu, co pozwala na kontynuowanie pracy przez stare odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-134">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="70ed7-135">Ten <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybut używa sygnatury licznika, aby upewnić się, że właściciel nowego klucza podpisu jest również właścicielem starego klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-135">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="70ed7-136">Podpisz przy użyciu algorytmu SHA-2 bez migracji klucza</span><span class="sxs-lookup"><span data-stu-id="70ed7-136">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="70ed7-137">Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw bez migrowania sygnatury silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="70ed7-137">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="70ed7-138">Generuj nowy klucz tożsamości (w razie potrzeby).</span><span class="sxs-lookup"><span data-stu-id="70ed7-138">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="70ed7-139">Wyodrębnij klucz publiczny tożsamości i określ, że algorytm SHA-2 powinien być używany podczas podpisywania przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="70ed7-139">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="70ed7-140">Opóźnij podpisanie zestawu przy użyciu pliku klucza publicznego tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-140">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="70ed7-141">Ponowne podpisywanie zestawu za pomocą pary kluczy pełnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-141">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="70ed7-142">Logowanie przy użyciu algorytmu SHA-2 z migracją klucza</span><span class="sxs-lookup"><span data-stu-id="70ed7-142">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="70ed7-143">Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw za pomocą zmigrowanego podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="70ed7-143">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="70ed7-144">Wygeneruj parę kluczy tożsamości i sygnatury (w razie potrzeby).</span><span class="sxs-lookup"><span data-stu-id="70ed7-144">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="70ed7-145">Wyodrębnij klucz publiczny podpisu i określ, że algorytm SHA-2 powinien być używany podczas podpisywania przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="70ed7-145">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="70ed7-146">Wyodrębnij klucz publiczny tożsamości, który określa algorytm wyznaczania wartości skrótu, który generuje sygnaturę licznika.</span><span class="sxs-lookup"><span data-stu-id="70ed7-146">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="70ed7-147">Generuj parametry dla <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybutu i Dołącz atrybut do zestawu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-147">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="70ed7-148">Daje to wynik podobny do poniższego.</span><span class="sxs-lookup"><span data-stu-id="70ed7-148">This produces output similar to the following.</span></span>

    ```output
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

    <span data-ttu-id="70ed7-149">Dane wyjściowe można następnie przekształcić do atrybucie AssemblySignatureKeyAttribute określono.</span><span class="sxs-lookup"><span data-stu-id="70ed7-149">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="70ed7-150">Opóźnij podpisanie zestawu przy użyciu klucza publicznego tożsamości.</span><span class="sxs-lookup"><span data-stu-id="70ed7-150">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="70ed7-151">W pełni podpisz zestaw za pomocą pary kluczy podpisu.</span><span class="sxs-lookup"><span data-stu-id="70ed7-151">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="70ed7-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70ed7-152">See also</span></span>

- [<span data-ttu-id="70ed7-153">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="70ed7-153">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
