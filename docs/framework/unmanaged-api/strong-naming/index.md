---
title: Silne nazewnictwo (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140632"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="3dcaf-102">Silne nazewnictwo (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="3dcaf-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="3dcaf-103">Interfejs API silnego nazewnictwa pozwala klientowi administrować podpisywaniem silnych nazw dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="3dcaf-104">Podpisanie zestawu silną nazwą dodaje szyfrowanie kluczem publicznym do pliku zawierającego manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="3dcaf-105">Podpisywanie silnej nazwy pomaga weryfikować unikatowość nazw, zapobiega fałszowaniu nazw i zapewnia wywołującym unikatową tożsamość, gdy odwołanie jest rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="3dcaf-106">Jednak żaden poziom zaufania nie jest skojarzony z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3dcaf-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3dcaf-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dcaf-108">Wszystkie te funkcje są przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="3dcaf-109">W przypadku sugerowanych alternatyw należy zapoznać się z interfejsem [ICLRStrongName](../hosting/iclrstrongname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3dcaf-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="3dcaf-110">GetHashFromAssemblyFile, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="3dcaf-111">Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="3dcaf-112">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-113">GetHashFromAssemblyFileW, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="3dcaf-114">Pobiera skrót pliku zestawu określony jako ciąg Unicode przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="3dcaf-115">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-116">GetHashFromBlob, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="3dcaf-117">Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="3dcaf-118">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-119">GetHashFromFile, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="3dcaf-120">Generuje skrót do zawartości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="3dcaf-121">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-122">GetHashFromFileW, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="3dcaf-123">Generuje skrót do zawartości pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="3dcaf-124">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-125">GetHashFromHandle, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="3dcaf-126">Generuje skrót do zawartości pliku z określonym dojściem do pliku przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="3dcaf-127">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-128">StrongNameCompareAssemblies, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="3dcaf-129">Określa, czy dwa zestawy różnią się tylko sygnaturami silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="3dcaf-130">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-131">StrongNameErrorInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="3dcaf-132">Pobiera kod ostatniego błędu, który został zgłoszony przez jedną z funkcji silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="3dcaf-133">StrongNameFreeBuffer, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="3dcaf-134">Zwalnia pamięć, która została przypisana przy użyciu poprzedniego wywołania funkcji silnej nazwy, takiej jak [StrongNameGetPublicKey —](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey —](strongnametokenfrompublickey-function.md)lub [StrongNameSignatureGeneration —](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="3dcaf-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="3dcaf-135">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-136">StrongNameGetBlob, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="3dcaf-137">Wypełnia określony bufor reprezentacją binarną pliku wykonywalnego pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="3dcaf-138">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-139">StrongNameGetBlobFromImage, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="3dcaf-140">Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="3dcaf-141">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-142">StrongNameGetPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="3dcaf-143">Pobiera klucz publiczny z pary kluczy prywatnych/publicznych.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="3dcaf-144">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-145">StrongNameHashSize, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="3dcaf-146">Pobiera rozmiar buforu wymagany dla skrótu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="3dcaf-147">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-148">StrongNameKeyDelete, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="3dcaf-149">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-149">Deletes the specified key container.</span></span> <span data-ttu-id="3dcaf-150">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-151">StrongNameKeyGen, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="3dcaf-152">Tworzy nową parę kluczy publiczny/prywatny w celu użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="3dcaf-153">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-154">StrongNameKeyGenEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="3dcaf-155">Generuje nową parę kluczy publicznych/prywatnych z określonym rozmiarem klucza w celu użycia silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="3dcaf-156">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-157">StrongNameKeyInstall, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="3dcaf-158">Importuje parę kluczy publiczny/prywatny do kontenera.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="3dcaf-159">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-160">StrongNameSignatureGeneration, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="3dcaf-161">Generuje podpis silnej nazwy dla określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="3dcaf-162">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-163">StrongNameSignatureGenerationEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="3dcaf-164">Generuje podpis silnej nazwy dla określonego zestawu, na podstawie określonych flag.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="3dcaf-165">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-166">StrongNameSignatureSize, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="3dcaf-167">Zwraca rozmiar sygnatury silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="3dcaf-168">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-169">StrongNameSignatureVerification, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="3dcaf-170">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera sygnaturę silnej nazwy, która jest sprawdzana według określonych flag.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="3dcaf-171">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-172">StrongNameSignatureVerificationEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="3dcaf-173">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="3dcaf-174">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-175">StrongNameSignatureVerificationFromImage, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="3dcaf-176">Sprawdza, czy zestaw, który został już zamapowany na pamięć, jest prawidłowy dla skojarzonego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="3dcaf-177">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-178">StrongNameTokenFromAssembly, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="3dcaf-179">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="3dcaf-180">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-181">StrongNameTokenFromAssemblyEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="3dcaf-182">Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="3dcaf-183">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-184">StrongNameTokenFromPublicKey, funkcja</span><span class="sxs-lookup"><span data-stu-id="3dcaf-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="3dcaf-185">Pobiera token reprezentujący klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-185">Gets a token representing a public key.</span></span> <span data-ttu-id="3dcaf-186">Przestarzałe, począwszy od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="3dcaf-187">PublicKeyBlob, struktura</span><span class="sxs-lookup"><span data-stu-id="3dcaf-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="3dcaf-188">Reprezentuje klucz publiczny pary kluczy publiczny/prywatny w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="3dcaf-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcaf-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3dcaf-189">See also</span></span>

- [<span data-ttu-id="3dcaf-190">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="3dcaf-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="3dcaf-191">Niezarządzane interfejsy API — informacje</span><span class="sxs-lookup"><span data-stu-id="3dcaf-191">Unmanaged API Reference</span></span>](../index.md)
