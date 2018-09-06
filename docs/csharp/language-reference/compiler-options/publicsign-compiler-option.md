---
title: -publicsign (opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 01ce30b9ac5997f56f29dcbbfa43a27738fa5556
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870449"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="a416d-102">-publicsign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a416d-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="a416d-103">Ta opcja powoduje, że kompilator zastosować klucz publiczny, ale nie faktycznego podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="a416d-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="a416d-104">**- Publicsign** również ustawia bit w zestawie, który informuje środowiska uruchomieniowego, w rzeczywistości podpisania pliku.</span><span class="sxs-lookup"><span data-stu-id="a416d-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="a416d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a416d-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="a416d-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a416d-106">Arguments</span></span>

<span data-ttu-id="a416d-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="a416d-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="a416d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a416d-108">Remarks</span></span>

<span data-ttu-id="a416d-109">**- Publicsign** opcja wymaga użycia [- keyfile](keyfile-compiler-option.md) lub [- keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a416d-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="a416d-110">**Keyfile** lub **keycontainer** opcji Określ klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="a416d-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="a416d-111">**- Publicsign** i **- delaysign** opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="a416d-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="a416d-112">Czasami nazywane "fałszywych znak" lub "OSS znak", publiczne podpisywanie zawiera klucz publiczny w zestawie danych wyjściowych i ustawia flagę "podpisem", ale faktycznie nie podpisać zestaw przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="a416d-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="a416d-113">Jest to przydatne w przypadku projektów "open source", gdzie użytkownicy chcą utworzyć zestawy, które są zgodne z wydana w zestawach "niecałkowicie podpisany", ale nie mają dostępu do prywatnego klucza używanego do podpisywania zestawów.</span><span class="sxs-lookup"><span data-stu-id="a416d-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="a416d-114">Ponieważ niemal żadnych użytkowników jest potrzebna do sprawdzenia, jeśli zestaw jest niecałkowicie podpisany, publicznie skompilowanych zestawów są niemożliwe w prawie w każdym scenariuszu, w której będzie służyć całkowicie podpisanego jeden.</span><span class="sxs-lookup"><span data-stu-id="a416d-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a416d-115">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a416d-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="a416d-116">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a416d-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="a416d-117">Modyfikowanie **opóźnienie logowania tylko** właściwości.</span><span class="sxs-lookup"><span data-stu-id="a416d-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="a416d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a416d-118">See Also</span></span>

- [<span data-ttu-id="a416d-119">-Delaysign — opcja kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a416d-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)  
- [<span data-ttu-id="a416d-120">-Keyfile — opcja kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a416d-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)  
- [<span data-ttu-id="a416d-121">Kompilator języka C# - keycontainer — opcja</span><span class="sxs-lookup"><span data-stu-id="a416d-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)  
- [<span data-ttu-id="a416d-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a416d-122">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="a416d-123">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a416d-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
