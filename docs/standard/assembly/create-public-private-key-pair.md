---
title: 'Jak: Tworzenie pary kluczy publiczno-prywatnych'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8a9845e3cd18ff86ec04216ad0e9c5606186b113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122519"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="60bdb-102">Jak: Tworzenie pary kluczy publiczno-prywatnych</span><span class="sxs-lookup"><span data-stu-id="60bdb-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="60bdb-103">Aby podpisać zestaw o silnej nazwie, musisz mieć parę kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="60bdb-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="60bdb-104">Ta publiczna i prywatna para kluczy kryptograficznych jest używana podczas kompilacji do tworzenia zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="60bdb-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="60bdb-105">Parę kluczy można utworzyć za pomocą [narzędzia Silna nazwa (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="60bdb-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="60bdb-106">Pliki pary kluczy mają zwykle rozszerzenie *.snk.*</span><span class="sxs-lookup"><span data-stu-id="60bdb-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="60bdb-107">W programie Visual Studio strony właściwości projektu Języka C# i Visual Basic zawierają kartę **Podpisywanie,** która umożliwia wybranie istniejących plików kluczy lub wygenerowanie nowych plików kluczy bez użycia *programu Sn.exe.*</span><span class="sxs-lookup"><span data-stu-id="60bdb-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="60bdb-108">W programie Visual C++ można określić lokalizację istniejącego pliku klucza na stronie **właściwości Zaawansowane** w sekcji **Właściwości** **konfiguracji** w oknie **Strony właściwości.**</span><span class="sxs-lookup"><span data-stu-id="60bdb-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="60bdb-109">Użycie atrybutu <xref:System.Reflection.AssemblyKeyFileAttribute> do identyfikowania par plików kluczy stało się przestarzałe począwszy od programu Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="60bdb-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="60bdb-110">Tworzenie pary kluczy</span><span class="sxs-lookup"><span data-stu-id="60bdb-110">Create a key pair</span></span>

<span data-ttu-id="60bdb-111">Aby utworzyć parę kluczy, w wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="60bdb-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="60bdb-112">*nazwa pliku* **sn –k** \<></span><span class="sxs-lookup"><span data-stu-id="60bdb-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="60bdb-113">W tym poleceniu *nazwa pliku* jest nazwą pliku wyjściowego zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="60bdb-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="60bdb-114">Poniższy przykład tworzy parę kluczy o nazwie *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="60bdb-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="60bdb-115">Jeśli zamierzasz opóźnić podpisanie zestawu i kontrolować całą parę kluczy (co jest mało prawdopodobne, scenariusze testów zewnętrznych), można użyć następujących poleceń do wygenerowania pary kluczy, a następnie wyodrębnić klucz publiczny z niego do oddzielnego pliku.</span><span class="sxs-lookup"><span data-stu-id="60bdb-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="60bdb-116">Najpierw utwórz parę kluczy:</span><span class="sxs-lookup"><span data-stu-id="60bdb-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="60bdb-117">Następnie wyodrębnij klucz publiczny z pary kluczy i skopiuj go do oddzielnego pliku:</span><span class="sxs-lookup"><span data-stu-id="60bdb-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="60bdb-118">Po utworzeniu pary kluczy należy umieścić plik, w którym można go znaleźć narzędzia do podpisywania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="60bdb-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="60bdb-119">Podczas podpisywania zestawu o silnej nazwie [konsolidator zestawu (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) wyszbędzie plik klucza względem bieżącego katalogu i katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="60bdb-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="60bdb-120">Korzystając z kompilatorów wiersza polecenia, można po prostu skopiować klucz do bieżącego katalogu zawierającego moduły kodu.</span><span class="sxs-lookup"><span data-stu-id="60bdb-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="60bdb-121">Jeśli używasz starszej wersji programu Visual Studio, która nie ma karty **Podpisywanie** we właściwościach projektu, zalecaną lokalizacją pliku klucza jest katalog projektu z atrybutem pliku określonym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="60bdb-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="60bdb-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60bdb-122">See also</span></span>

- [<span data-ttu-id="60bdb-123">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="60bdb-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
