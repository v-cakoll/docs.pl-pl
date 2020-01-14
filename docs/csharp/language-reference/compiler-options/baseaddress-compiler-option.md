---
title: -BaseAddress (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937211"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="3a9a5-102">-BaseAddress (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3a9a5-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="3a9a5-103">Opcja **-BaseAddress** pozwala określić preferowany adres podstawowy, przy użyciu którego ma zostać ZAŁADOWANA Biblioteka DLL.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="3a9a5-104">Aby uzyskać więcej informacji na temat tego, kiedy i dlaczego należy używać tej opcji, zobacz [dziennik sieci Web Larry Osterman](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="3a9a5-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9a5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a9a5-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a9a5-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3a9a5-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="3a9a5-107">Adres podstawowy biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-107">The base address for the DLL.</span></span> <span data-ttu-id="3a9a5-108">Ten adres można określić jako liczbę dziesiętną, szesnastkową lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a9a5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a9a5-109">Remarks</span></span>  
 <span data-ttu-id="3a9a5-110">Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="3a9a5-111">Należy pamiętać, że Dolna kolejność wyrazów w tym adresie zostanie zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="3a9a5-112">Na przykład, jeśli określisz 0x11110001, zostanie ona zaokrąglona do 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="3a9a5-113">Aby ukończyć proces podpisywania dla biblioteki DLL, Użyj SN. EXE z opcją-R.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3a9a5-114">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3a9a5-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3a9a5-115">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="3a9a5-116">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="3a9a5-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="3a9a5-117">Kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="3a9a5-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="3a9a5-118">Zmodyfikuj właściwość **adresu podstawowego biblioteki DLL** .</span><span class="sxs-lookup"><span data-stu-id="3a9a5-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="3a9a5-119">Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a9a5-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9a5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a9a5-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3a9a5-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3a9a5-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3a9a5-122">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3a9a5-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
