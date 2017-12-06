---
title: -baseaddress (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8cc5e19565a0e5044626c4fb8eb9d684fbe0a73
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2017
---
# <a name="baseaddress-c-compiler-options"></a><span data-ttu-id="691de-102">/baseaddress (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="691de-102">/baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="691de-103">**/BaseAddress** pozwala określić preferowany adres podstawowy, w którym można załadować biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="691de-103">The **/baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="691de-104">Aby uzyskać więcej informacji na temat kiedy i dlaczego użyć tej opcji, zobacz [WebLog Larry Ostermana](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="691de-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="691de-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="691de-105">Syntax</span></span>  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="691de-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="691de-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="691de-107">Adres podstawowy biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="691de-107">The base address for the DLL.</span></span> <span data-ttu-id="691de-108">Ten adres można określić jako liczbę szesnastkową lub ósemkowo dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="691de-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="691de-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="691de-109">Remarks</span></span>  
 <span data-ttu-id="691de-110">Domyślny adres podstawowy biblioteki DLL jest ustawiana przez .NET Framework środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="691de-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="691de-111">Należy pamiętać, zostanie zaokrąglony word kolejności dolna ten adres.</span><span class="sxs-lookup"><span data-stu-id="691de-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="691de-112">Na przykład jeśli określisz 0x11110001, zostanie on zaokrąglony do 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="691de-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="691de-113">Aby ukończyć proces podpisywania dla biblioteki DLL, użyj SN. EXE z opcją -R.</span><span class="sxs-lookup"><span data-stu-id="691de-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="691de-114">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="691de-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="691de-115">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="691de-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="691de-116">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="691de-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="691de-117">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="691de-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="691de-118">Modyfikowanie **adres podstawowy DLL** właściwości.</span><span class="sxs-lookup"><span data-stu-id="691de-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="691de-119">Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="691de-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691de-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="691de-120">See Also</span></span>  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="691de-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="691de-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="691de-122">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="691de-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
