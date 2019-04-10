---
title: 'Instrukcje: Tworzenie pary kluczy publiczny-prywatny'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71eaaa85b8bd287c37f59116e75cf99b030d63ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297840"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="26e1c-102">Instrukcje: Tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="26e1c-102">How to: Create a Public-Private Key Pair</span></span>

<span data-ttu-id="26e1c-103">Aby podpisać zestaw silną nazwą, musisz mieć parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="26e1c-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="26e1c-104">Ta publicznych i prywatnych z pary kluczy kryptograficznych jest używany podczas kompilacji do tworzenia zestawu z silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="26e1c-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="26e1c-105">Możesz utworzyć parę kluczy, używając [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="26e1c-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="26e1c-106">Pliki par kluczy mają zwykle rozszerzenie .snk.</span><span class="sxs-lookup"><span data-stu-id="26e1c-106">Key pair files usually have an .snk extension.</span></span>

> [!NOTE]
> <span data-ttu-id="26e1c-107">W programie Visual Studio obejmują strony właściwości projektu C# i Visual Basic **podpisywanie** kartę, która pozwala wybrać istniejące pliki klucza lub do generowania nowych kluczy plików bez użycia Sn.exe.</span><span class="sxs-lookup"><span data-stu-id="26e1c-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using Sn.exe.</span></span> <span data-ttu-id="26e1c-108">W programie Visual C++, należy określić lokalizację istniejącego pliku klucza w **zaawansowane** — strona właściwości w **konsolidatora** części **właściwości konfiguracji** sekcji **Stron właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="26e1c-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="26e1c-109">Korzystanie z <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut do identyfikowania pary pliku klucza stało się przestarzałe, począwszy od programu Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="26e1c-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs has been made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="to-create-a-key-pair"></a><span data-ttu-id="26e1c-110">Aby utworzyć parę kluczy</span><span class="sxs-lookup"><span data-stu-id="26e1c-110">To create a key pair</span></span>

1. <span data-ttu-id="26e1c-111">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="26e1c-111">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="26e1c-112">**numery seryjne – k** \< *nazwy pliku*></span><span class="sxs-lookup"><span data-stu-id="26e1c-112">**sn –k** \<*file name*></span></span>

     <span data-ttu-id="26e1c-113">W tym poleceniu *nazwy pliku* to nazwa pliku wyjściowego zawierającego parę kluczy.</span><span class="sxs-lookup"><span data-stu-id="26e1c-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

 <span data-ttu-id="26e1c-114">Poniższy przykład tworzy parę kluczy o nazwie `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="26e1c-114">The following example creates a key pair called `sgKey.snk`.</span></span>

```
sn -k sgKey.snk
```

 <span data-ttu-id="26e1c-115">Jeśli zamierzasz opóźnienie Podpisz zestaw i kontrolować pary zupełnie kluczy, (która jest mało prawdopodobne, poza scenariuszy testowania), należy użyć następującego polecenia do wygeneruj parę kluczy, a następnie wyodrębnić klucza publicznego z niego w osobnym pliku.</span><span class="sxs-lookup"><span data-stu-id="26e1c-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="26e1c-116">Najpierw Utwórz parę kluczy:</span><span class="sxs-lookup"><span data-stu-id="26e1c-116">First, create the key pair:</span></span>

```
sn -k keypair.snk
```

 <span data-ttu-id="26e1c-117">Następnie Wyodrębnij klucz publiczny z pary kluczy i skopiuj go do osobnego pliku:</span><span class="sxs-lookup"><span data-stu-id="26e1c-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```
sn -p keypair.snk public.snk
```

 <span data-ttu-id="26e1c-118">Po utworzeniu parę kluczy, należy umieścić plik, gdzie podpisywania narzędzia silnymi nazwami mogła go odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="26e1c-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

 <span data-ttu-id="26e1c-119">Przy podpisywaniu zestawu silną nazwą [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) szuka klucza pliku względną do bieżącego katalogu i do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="26e1c-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="26e1c-120">Korzystając z kompilatorów wiersza polecenia, można po prostu skopiować klucz do bieżącego katalogu zawierającego moduły kodu.</span><span class="sxs-lookup"><span data-stu-id="26e1c-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

 <span data-ttu-id="26e1c-121">Jeśli używasz starszej wersji programu Visual Studio, który nie ma **podpisywanie** karcie we właściwościach projektu lokalizacji pliku klucza zalecane jest katalogu projektu za pomocą atrybutu pliku określona w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="26e1c-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a><span data-ttu-id="26e1c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26e1c-122">See also</span></span>

- [<span data-ttu-id="26e1c-123">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="26e1c-123">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
