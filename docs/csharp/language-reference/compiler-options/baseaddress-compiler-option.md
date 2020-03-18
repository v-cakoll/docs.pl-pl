---
title: -baseaddress (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937211"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="e695b-102">-baseaddress (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="e695b-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="e695b-103">Opcja **-baseaddress** umożliwia określenie preferowanego adresu podstawowego, pod którym ma zostać załadowana dll.</span><span class="sxs-lookup"><span data-stu-id="e695b-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="e695b-104">Aby uzyskać więcej informacji o tym, kiedy i dlaczego warto użyć tej opcji, zobacz [Logowanie Larry'ego Ostermana](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="e695b-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e695b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e695b-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="e695b-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e695b-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="e695b-107">Adres podstawowy dla pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="e695b-107">The base address for the DLL.</span></span> <span data-ttu-id="e695b-108">Ten adres można określić jako liczbę dziesiętną, szesnastkową lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="e695b-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e695b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e695b-109">Remarks</span></span>  
 <span data-ttu-id="e695b-110">Domyślny adres podstawowy dla dll jest ustawiany przez program runtime wspólnego języka .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e695b-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="e695b-111">Należy pamiętać, że słowo niższego rzędu w tym adresie zostanie zaokrąglone.</span><span class="sxs-lookup"><span data-stu-id="e695b-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="e695b-112">Na przykład jeśli określisz 0x11110001, zostanie zaokrąglony do 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="e695b-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="e695b-113">Aby zakończyć proces podpisywania dla dll, należy użyć sn. EXE z opcją -R.</span><span class="sxs-lookup"><span data-stu-id="e695b-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e695b-114">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e695b-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e695b-115">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="e695b-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e695b-116">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="e695b-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="e695b-117">Kliknij przycisk **Zaawansowane.**</span><span class="sxs-lookup"><span data-stu-id="e695b-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="e695b-118">Zmodyfikuj właściwość **DLL Base Address.**</span><span class="sxs-lookup"><span data-stu-id="e695b-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="e695b-119">Aby programowo ustawić tę opcję <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="e695b-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e695b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e695b-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e695b-121">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="e695b-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e695b-122">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="e695b-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
