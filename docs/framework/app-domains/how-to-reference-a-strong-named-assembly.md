---
title: 'Instrukcje: Odwołanie do zestawu o silnej nazwie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 281cfa6507d293658e436a95a5ded0174154a13c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301025"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="39652-102">Instrukcje: Odwołanie do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="39652-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="39652-103">Proces odwołania do typów lub zasoby znajdujące się zestawu z silną nazwą jest zazwyczaj niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="39652-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="39652-104">Istnieje możliwość odwołania w czasie kompilacji (wczesne powiązania) lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="39652-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="39652-105">Odwołanie kompilacji występuje, gdy w kompilatorze wskazujesz, że zestaw jawnie odwoływać się do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="39652-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="39652-106">Gdy używasz odwołujące się do kompilacji, kompilator automatycznie pobiera klucz publiczny zestawu o silnej nazwie docelowych i umieszcza je w zestawu kompilowanego odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="39652-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39652-107">Zestaw o silnej nazwie można używać tylko typów od innych zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="39652-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="39652-108">W przeciwnym razie zabezpieczeń zestawu o silnej nazwie może być narażone na ataki.</span><span class="sxs-lookup"><span data-stu-id="39652-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="39652-109">Kompilacji odwołać się do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="39652-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="39652-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="39652-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="39652-111">\<*polecenie kompilatora*> **/reference:**\<*nazwy zestawu*></span><span class="sxs-lookup"><span data-stu-id="39652-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="39652-112">W tym poleceniu *polecenia kompilatora* polecenia kompilatora dla języka, którego używasz, i *nazwy zestawu* to nazwa zestawu o silnej nazwie, do którego nastąpiło odwołanie.</span><span class="sxs-lookup"><span data-stu-id="39652-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="39652-113">Umożliwia także inne opcje kompilatora, takich jak **/t** opcją w przypadku tworzenia zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="39652-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="39652-114">Poniższy przykład tworzy zestaw o nazwie `myAssembly.dll` odwołuje się zestaw o silnej nazwie, o nazwie `myLibAssembly.dll` moduł kodu o nazwie `myAssembly.cs`.</span><span class="sxs-lookup"><span data-stu-id="39652-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="39652-115">Zapewnienie środowiska wykonawczego odwołanie do zestawu z silną nazwą</span><span class="sxs-lookup"><span data-stu-id="39652-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="39652-116">Po ustawieniu środowiska wykonawczego odwołanie do zestawu z silną nazwą (na przykład za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metoda), należy użyć nazwy wyświetlania przywoływanego zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="39652-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="39652-117">Składnia Nazwa wyświetlana jest następująca:</span><span class="sxs-lookup"><span data-stu-id="39652-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="39652-118">\<*Nazwa zestawu*>**,** \< *numer wersji*>**,** \< *kultury*  > **,** \< *token klucza publicznego*></span><span class="sxs-lookup"><span data-stu-id="39652-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="39652-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="39652-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="39652-120">W tym przykładzie `PublicKeyToken` jest szesnastkowe formą token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="39652-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="39652-121">Jeśli nie istnieje wartość kultury, należy użyć `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="39652-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="39652-122">Poniższy przykład kodu pokazuje, jak dzięki tym informacjom o <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="39652-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="39652-123">Można wydrukować szesnastkowej klucz publiczny i token klucza publicznego dla określonego zestawu przy użyciu następujących [silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="39652-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="39652-124">**SN - Tp \<**  *zestawu* **>**</span><span class="sxs-lookup"><span data-stu-id="39652-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="39652-125">Jeśli masz plik klucza publicznego, należy użyć następującego polecenia (należy zauważyć różnicę w przypadku opcji wiersza polecenia):</span><span class="sxs-lookup"><span data-stu-id="39652-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="39652-126">**SN - tp \<**  *pliku klucza publicznego* **>**</span><span class="sxs-lookup"><span data-stu-id="39652-126">**sn -tp \<** *public key file* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39652-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39652-127">See also</span></span>

- [<span data-ttu-id="39652-128">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="39652-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
