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
ms.openlocfilehash: 7cd3269754f783ab8b26683f5215aa81825673e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress-c-compiler-options"></a><span data-ttu-id="4e796-102">/baseaddress (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4e796-102">/baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="4e796-103">**/BaseAddress** pozwala określić preferowany adres podstawowy, w którym można załadować biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="4e796-103">The **/baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="4e796-104">Aby uzyskać więcej informacji na temat kiedy i dlaczego użyć tej opcji, zobacz [WebLog Larry Ostermana](http://go.microsoft.com/fwlink/?LinkId=107044).</span><span class="sxs-lookup"><span data-stu-id="4e796-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](http://go.microsoft.com/fwlink/?LinkId=107044).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e796-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e796-105">Syntax</span></span>  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e796-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4e796-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="4e796-107">Adres podstawowy biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="4e796-107">The base address for the DLL.</span></span> <span data-ttu-id="4e796-108">Ten adres można określić jako liczbę szesnastkową lub ósemkowo dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="4e796-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e796-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e796-109">Remarks</span></span>  
 <span data-ttu-id="4e796-110">Domyślny adres podstawowy biblioteki DLL jest ustawiana przez .NET Framework środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4e796-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="4e796-111">Należy pamiętać, zostanie zaokrąglony word kolejności dolna ten adres.</span><span class="sxs-lookup"><span data-stu-id="4e796-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="4e796-112">Na przykład jeśli określisz 0x11110001, zostanie on zaokrąglony do 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="4e796-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="4e796-113">Aby ukończyć proces podpisywania dla biblioteki DLL, użyj SN. EXE z opcją -R.</span><span class="sxs-lookup"><span data-stu-id="4e796-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4e796-114">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4e796-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4e796-115">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="4e796-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="4e796-116">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e796-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="4e796-117">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4e796-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="4e796-118">Modyfikowanie **adres podstawowy DLL** właściwości.</span><span class="sxs-lookup"><span data-stu-id="4e796-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="4e796-119">Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e796-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e796-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e796-120">See Also</span></span>  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4e796-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="4e796-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4e796-122">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="4e796-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
