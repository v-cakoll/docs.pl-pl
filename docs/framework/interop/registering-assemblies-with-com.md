---
title: "Rejestrowanie zestawów do użycia z modelem COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1473fa07b57dcd19ea192db6cdb0a395f119b159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="70e07-102">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="70e07-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="70e07-103">Można uruchomić narzędzie wiersza polecenia o nazwie [narzędzie rejestracji zestawów (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) do zarejestrowania lub wyrejestrowania zestawu do użytku z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="70e07-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="70e07-104">Regasm.exe dodaje informacje o klasie w rejestrze systemu, więc klientów modelu COM można użyć klasy .NET Framework w sposób niewidoczny dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70e07-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="70e07-105"><xref:System.Runtime.InteropServices.RegistrationServices> Klasa udostępnia podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="70e07-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="70e07-106">Zanim można aktywować z klient modelu COM, w rejestrze systemu Windows należy zarejestrować zarządzanego składnika.</span><span class="sxs-lookup"><span data-stu-id="70e07-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="70e07-107">W poniższej tabeli przedstawiono kluczy, które Regasm.exe zazwyczaj dodaje do rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="70e07-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="70e07-108">(000000 wskazuje rzeczywistą wartość identyfikatora GUID).</span><span class="sxs-lookup"><span data-stu-id="70e07-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="70e07-109">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="70e07-109">GUID</span></span>|<span data-ttu-id="70e07-110">Opis</span><span class="sxs-lookup"><span data-stu-id="70e07-110">Description</span></span>|<span data-ttu-id="70e07-111">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="70e07-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="70e07-112">IDENTYFIKATOR CLSID</span><span class="sxs-lookup"><span data-stu-id="70e07-112">CLSID</span></span>|<span data-ttu-id="70e07-113">Identyfikator klasy</span><span class="sxs-lookup"><span data-stu-id="70e07-113">Class identifier</span></span>|<span data-ttu-id="70e07-114">HKEY_CLASSES_ROOT\CLSID\\{000... 000}</span><span class="sxs-lookup"><span data-stu-id="70e07-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="70e07-115">IDENTYFIKATOR IID</span><span class="sxs-lookup"><span data-stu-id="70e07-115">IID</span></span>|<span data-ttu-id="70e07-116">Identyfikator interfejsu</span><span class="sxs-lookup"><span data-stu-id="70e07-116">Interface identifier</span></span>|<span data-ttu-id="70e07-117">HKEY_CLASSES_ROOT\Interface\\{000... 000}</span><span class="sxs-lookup"><span data-stu-id="70e07-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="70e07-118">IDENTYFIKATOR BIBLIOTEKI</span><span class="sxs-lookup"><span data-stu-id="70e07-118">LIBID</span></span>|<span data-ttu-id="70e07-119">Identyfikator biblioteki</span><span class="sxs-lookup"><span data-stu-id="70e07-119">Library identifier</span></span>|<span data-ttu-id="70e07-120">HKEY_CLASSES_ROOT\TypeLib\\{000... 000}</span><span class="sxs-lookup"><span data-stu-id="70e07-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="70e07-121">Identyfikator programu</span><span class="sxs-lookup"><span data-stu-id="70e07-121">ProgID</span></span>|<span data-ttu-id="70e07-122">Identyfikator programowy</span><span class="sxs-lookup"><span data-stu-id="70e07-122">Programmatic identifier</span></span>|<span data-ttu-id="70e07-123">HKEY_CLASSES_ROOT\000... 000</span><span class="sxs-lookup"><span data-stu-id="70e07-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="70e07-124">W obszarze HKCR\CLSID\\{0000... 0000} klucza, wartość domyślna jest równa ProgID klasy i zostaną dodane dwa nowe nazwanych wartości, klasy i zestawu.</span><span class="sxs-lookup"><span data-stu-id="70e07-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="70e07-125">Środowisko uruchomieniowe odczytuje wartość zestawu z rejestru i przekazywane do rozpoznawania zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="70e07-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="70e07-126">Mechanizm rozpoznawania zestawów próbuje zlokalizować zestawu, na podstawie zestawu informacji takich jak nazwa i numer wersji.</span><span class="sxs-lookup"><span data-stu-id="70e07-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="70e07-127">Dla rozpoznawania zestawu do zlokalizowania zestawu zestawu musi być w jednym z następujących lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="70e07-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="70e07-128">Globalna pamięć podręczna zestawów (musi być to zestaw o silnej nazwie).</span><span class="sxs-lookup"><span data-stu-id="70e07-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="70e07-129">W katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70e07-129">In the application directory.</span></span> <span data-ttu-id="70e07-130">Zestawów załadowanych w ścieżce aplikacji są dostępne jedynie z tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70e07-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="70e07-131">Wzdłuż ścieżki pliku określony za pomocą **/ codebase** możliwość Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="70e07-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="70e07-132">Regasm.exe tworzy także klucz InProcServer32 w HKCR\CLSID\\{0000... 0000} klucz.</span><span class="sxs-lookup"><span data-stu-id="70e07-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="70e07-133">Wartość domyślna dla klucza ma ustawioną nazwę biblioteki dll, która inicjuje środowisko uruchomieniowe języka wspólnego (Mscoree.dll).</span><span class="sxs-lookup"><span data-stu-id="70e07-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="70e07-134">Badanie wpisów rejestru</span><span class="sxs-lookup"><span data-stu-id="70e07-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="70e07-135">Współdziałanie z COM udostępnia implementację fabryki klasy standardowych można utworzyć wystąpienia każdej klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70e07-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="70e07-136">Klienci mogą wywoływać **metody DllGetClassObject** na zarządzanej biblioteki DLL, aby otrzymać fabrykę klas i tworzenie obiektów, podobnie jak inne składnika COM.</span><span class="sxs-lookup"><span data-stu-id="70e07-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="70e07-137">Aby uzyskać `InprocServer32` podklucza, zamiast tradycyjnych Biblioteka typów COM, aby wskazać, że środowisko uruchomieniowe języka wspólnego tworzy obiekt zarządzany pojawi się odwołanie do biblioteki Mscoree.dll.</span><span class="sxs-lookup"><span data-stu-id="70e07-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e07-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70e07-138">See Also</span></span>  
 [<span data-ttu-id="70e07-139">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="70e07-139">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="70e07-140">Instrukcje: Odwołania do typów .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="70e07-140">How to: Reference .NET Types from COM</span></span>](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
 [<span data-ttu-id="70e07-141">Wywołanie obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="70e07-141">Calling a .NET Object</span></span>](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="70e07-142">Wdrażanie aplikacji na potrzeby dostępu modelu COM</span><span class="sxs-lookup"><span data-stu-id="70e07-142">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
