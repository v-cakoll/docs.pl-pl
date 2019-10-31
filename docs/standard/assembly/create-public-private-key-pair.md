---
title: 'Instrukcje: Tworzenie pary kluczy publiczny-prywatny'
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122519"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="695db-102">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="695db-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="695db-103">Aby podpisać zestaw za pomocą silnej nazwy, musisz mieć parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="695db-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="695db-104">Ta para publicznych i prywatnych kluczy kryptograficznych jest używana podczas kompilacji w celu utworzenia zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="695db-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="695db-105">Parę kluczy można utworzyć za pomocą [Narzędzia silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="695db-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="695db-106">Pliki pary kluczy zazwyczaj mają rozszerzenie *. snk* .</span><span class="sxs-lookup"><span data-stu-id="695db-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="695db-107">W programie Visual Studio strony C# właściwości projektu i Visual Basic zawierają kartę **podpisywanie** , która umożliwia wybieranie istniejących plików kluczy lub generowanie nowych plików kluczy bez korzystania z *SN. exe*.</span><span class="sxs-lookup"><span data-stu-id="695db-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="695db-108">W C++wizualizacji, możesz określić lokalizację istniejącego pliku klucza na stronie właściwości **Zaawansowane** w sekcji **konsolidator** w sekcji **Właściwości konfiguracji** w oknie **strony właściwości** .</span><span class="sxs-lookup"><span data-stu-id="695db-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="695db-109">Użycie atrybutu <xref:System.Reflection.AssemblyKeyFileAttribute> do identyfikowania par plików kluczy było przestarzałe, począwszy od programu Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="695db-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="695db-110">Tworzenie pary kluczy</span><span class="sxs-lookup"><span data-stu-id="695db-110">Create a key pair</span></span>

<span data-ttu-id="695db-111">Aby utworzyć parę kluczy, w wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="695db-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="695db-112">**SN —** *Nazwa pliku* \<k></span><span class="sxs-lookup"><span data-stu-id="695db-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="695db-113">W tym poleceniu *Nazwa pliku* jest nazwą pliku wyjściowego zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="695db-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="695db-114">Poniższy przykład tworzy parę kluczy o nazwie *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="695db-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="695db-115">Jeśli zamierzasz opóźnić podpisywanie zestawu i kontrolować całą parę kluczy (najprawdopodobniej poza scenariuszami testowymi), możesz użyć poniższych poleceń, aby wygenerować parę kluczy, a następnie wyodrębnić z niej klucz publiczny do osobnego pliku.</span><span class="sxs-lookup"><span data-stu-id="695db-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="695db-116">Najpierw Utwórz parę kluczy:</span><span class="sxs-lookup"><span data-stu-id="695db-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="695db-117">Następnie wyodrębnij klucz publiczny z pary kluczy i skopiuj go do oddzielnego pliku:</span><span class="sxs-lookup"><span data-stu-id="695db-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="695db-118">Po utworzeniu pary kluczy należy umieścić w niej plik, w którym znajdują się narzędzia podpisywania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="695db-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="695db-119">Podczas podpisywania zestawu o silnej nazwie [konsolidator zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) wyszukuje plik klucza względem bieżącego katalogu i do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="695db-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="695db-120">Używając kompilatorów wiersza polecenia, można po prostu skopiować klucz do bieżącego katalogu zawierającego moduły kodu.</span><span class="sxs-lookup"><span data-stu-id="695db-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="695db-121">Jeśli używasz wcześniejszej wersji programu Visual Studio, która nie ma karty **podpisywanie** we właściwościach projektu, zalecana lokalizacja pliku klucza jest katalogiem projektu z atrybutem pliku określonym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="695db-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="695db-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="695db-122">See also</span></span>

- [<span data-ttu-id="695db-123">Tworzenie i używanie zestawów o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="695db-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
