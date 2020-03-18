---
title: Poprawa silnego nazywania
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141168"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="5fb27-102">Poprawa silnego nazywania</span><span class="sxs-lookup"><span data-stu-id="5fb27-102">Enhanced strong naming</span></span>
<span data-ttu-id="5fb27-103">Podpis silnej nazwy jest mechanizmtożsamości w .NET Framework do identyfikowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="5fb27-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="5fb27-104">Jest to podpis cyfrowy klucza publicznego, który jest zwykle używany do weryfikacji integralności danych przekazywanych z inicjator (sygnatariusz) do odbiorcy (weryfikatora).</span><span class="sxs-lookup"><span data-stu-id="5fb27-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="5fb27-105">Ten podpis jest używany jako unikatowa tożsamość dla zestawu i zapewnia, że odwołania do zestawu nie są niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="5fb27-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="5fb27-106">Zestaw jest podpisany jako część procesu kompilacji, a następnie weryfikowany po załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="5fb27-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="5fb27-107">Silne podpisy nazw zapobiegają manipulowaniu przez złośliwe strony zestawem, a następnie ponownepodpisywanie zestawu przy użyciu klucza oryginalnego sygnatariusza.</span><span class="sxs-lookup"><span data-stu-id="5fb27-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="5fb27-108">Jednak silne klucze nazw nie zawierają żadnych wiarygodnych informacji o wydawcy, ani nie zawierają hierarchii certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="5fb27-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="5fb27-109">Silny podpis nie gwarantuje wiarygodności osoby, która podpisała zgromadzenie, ani nie wskazuje, czy osoba ta była prawowitym właścicielem klucza; wskazuje tylko, że właściciel klucza podpisał zestaw.</span><span class="sxs-lookup"><span data-stu-id="5fb27-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="5fb27-110">W związku z tym nie zaleca się używania podpisu silnej nazwy jako sprawdzania poprawności zabezpieczeń dla ufania kodowi innej firmy.</span><span class="sxs-lookup"><span data-stu-id="5fb27-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="5fb27-111">Microsoft Authenticode to zalecany sposób uwierzytelniania kodu.</span><span class="sxs-lookup"><span data-stu-id="5fb27-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="5fb27-112">Ograniczenia konwencjonalnych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="5fb27-112">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="5fb27-113">Technologia silnego nazewnictwa używana w wersjach przed .NET Framework 4.5 ma następujące wady:</span><span class="sxs-lookup"><span data-stu-id="5fb27-113">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="5fb27-114">Klucze są stale atakowane, a ulepszone techniki i sprzęt ułatwiają wywnioskowanie klucza prywatnego z klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="5fb27-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="5fb27-115">Aby zabezpieczyć się przed atakami, konieczne są większe klucze.</span><span class="sxs-lookup"><span data-stu-id="5fb27-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="5fb27-116">Wersje .NET Framework przed .NET Framework 4.5 zapewniają możliwość podpisywania za pomocą dowolnego klucza rozmiaru (domyślny rozmiar to 1024 bity), ale podpisywanie zestawu za pomocą nowego klucza przerywa wszystkie pliki binarne, które odwołują się do starszej tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="5fb27-116">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="5fb27-117">W związku z tym jest niezwykle trudne do uaktualnienia rozmiar klucza podpisywania, jeśli chcesz zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="5fb27-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="5fb27-118">Podpisywanie silnej nazwy obsługuje tylko algorytm SHA-1.</span><span class="sxs-lookup"><span data-stu-id="5fb27-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="5fb27-119">Sha-1 niedawno stwierdzono, że nie odpowiednie dla bezpiecznych aplikacji mieszania.</span><span class="sxs-lookup"><span data-stu-id="5fb27-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="5fb27-120">W związku z tym silniejszy algorytm (SHA-256 lub więcej) jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="5fb27-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="5fb27-121">Jest możliwe, że SHA-1 straci swoją pozycję zgodną ze standardem FIPS, co stanowiłoby problemy dla tych, którzy zdecydują się używać tylko oprogramowania i algorytmów zgodnych z FIPS.</span><span class="sxs-lookup"><span data-stu-id="5fb27-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="5fb27-122">Zalety wzmocnionych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="5fb27-122">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="5fb27-123">Główne zalety wzmocnionych silnych nazw to zgodność z istniejącymi wcześniej silnymi nazwami i możliwość twierdzenia, że jedna tożsamość jest równoważna innej:</span><span class="sxs-lookup"><span data-stu-id="5fb27-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="5fb27-124">Deweloperzy, którzy mają wcześniej podpisane zestawy można migrować ich tożsamości do algorytmów SHA-2 przy zachowaniu zgodności z zestawów, które odwołują się do starych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="5fb27-125">Deweloperzy, którzy tworzą nowe zestawy i nie są zaniepokojeni wcześniej istniejących podpisów silnej nazwy można użyć bardziej bezpieczne algorytmy SHA-2 i podpisać zestawy, jak zawsze mają.</span><span class="sxs-lookup"><span data-stu-id="5fb27-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="5fb27-126">Używanie rozszerzonych silnych nazw</span><span class="sxs-lookup"><span data-stu-id="5fb27-126">Use enhanced strong names</span></span>  
 <span data-ttu-id="5fb27-127">Silne klucze nazw składają się z klucza podpisu i klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="5fb27-128">Zestaw jest podpisany przy pomocą klucza podpisu i jest identyfikowany przez klucz tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="5fb27-129">Przed .NET Framework 4.5 te dwa klucze były identyczne.</span><span class="sxs-lookup"><span data-stu-id="5fb27-129">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="5fb27-130">Począwszy od .NET Framework 4.5, klucz tożsamości pozostaje taki sam jak we wcześniejszych wersjach .NET Framework, ale klucz podpisu jest rozszerzony o silniejszy algorytm mieszania.</span><span class="sxs-lookup"><span data-stu-id="5fb27-130">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="5fb27-131">Ponadto klucz podpisu jest podpisany przy pomocą klucza tożsamości w celu utworzenia kontrpodpisu.</span><span class="sxs-lookup"><span data-stu-id="5fb27-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="5fb27-132">Atrybut <xref:System.Reflection.AssemblySignatureKeyAttribute> umożliwia metadanych zestawu do korzystania z istniejącego klucza publicznego dla tożsamości zestawu, co pozwala stare odwołania do zestawu, aby kontynuować pracę.</span><span class="sxs-lookup"><span data-stu-id="5fb27-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="5fb27-133">Atrybut <xref:System.Reflection.AssemblySignatureKeyAttribute> używa kontrpodpisu, aby upewnić się, że właściciel nowego klucza podpisu jest również właścicielem starego klucza tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="5fb27-134">Podpisz za pomocą SHA-2 bez migracji kluczy</span><span class="sxs-lookup"><span data-stu-id="5fb27-134">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="5fb27-135">Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw bez migracji podpisu silnej nazwy:</span><span class="sxs-lookup"><span data-stu-id="5fb27-135">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="5fb27-136">Wygeneruj nowy klucz tożsamości (jeśli to konieczne).</span><span class="sxs-lookup"><span data-stu-id="5fb27-136">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="5fb27-137">Wyodrębnij klucz publiczny tożsamości i określ, że algorytm SHA-2 powinien być używany podczas podpisywania za pomocą tego klucza.</span><span class="sxs-lookup"><span data-stu-id="5fb27-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="5fb27-138">Delay-sign zestawu z pliku klucza publicznego tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="5fb27-139">Ponownie podpisz zestaw za pomocą pełnej pary kluczy tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="5fb27-140">Podpisz za pomocą SHA-2 z migracją kluczy</span><span class="sxs-lookup"><span data-stu-id="5fb27-140">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="5fb27-141">Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw z migrowanym podpisem silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5fb27-141">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="5fb27-142">Generowanie pary kluczy tożsamości i podpisu (jeśli to konieczne).</span><span class="sxs-lookup"><span data-stu-id="5fb27-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="5fb27-143">Wyodrębnij klucz publiczny podpisu i określ, że algorytm SHA-2 powinien być używany podczas podpisywania za pomocą tego klucza.</span><span class="sxs-lookup"><span data-stu-id="5fb27-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="5fb27-144">Wyodrębnij klucz publiczny tożsamości, który określa algorytm mieszania, który generuje kontrpodpis.</span><span class="sxs-lookup"><span data-stu-id="5fb27-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="5fb27-145">Wygeneruj <xref:System.Reflection.AssemblySignatureKeyAttribute> parametry atrybutu i dołącz atrybut do złożenia.</span><span class="sxs-lookup"><span data-stu-id="5fb27-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="5fb27-146">Daje to dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="5fb27-146">This produces output similar to the following.</span></span>

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

    <span data-ttu-id="5fb27-147">Dane wyjściowe można następnie przekształcić w AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="5fb27-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="5fb27-148">Delay-sign zestawu z kluczem publicznym tożsamości.</span><span class="sxs-lookup"><span data-stu-id="5fb27-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="5fb27-149">W pełni podpisać zestaw z pary kluczy podpisu.</span><span class="sxs-lookup"><span data-stu-id="5fb27-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5fb27-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fb27-150">See also</span></span>

- [<span data-ttu-id="5fb27-151">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="5fb27-151">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
