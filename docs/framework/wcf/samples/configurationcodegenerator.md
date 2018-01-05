---
title: ConfigurationCodeGenerator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06885494f944a916671125a57132bd3ae706a79d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="aec2a-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="aec2a-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="aec2a-103">ConfigurationCodeGenerator to narzędzie, które można użyć do udostępnienia implementacjach użytkownika niestandardowego kanału do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="aec2a-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="aec2a-104">Pozwala to użytkownikom niestandardowego kanału skonfigurować kanał przy użyciu pliku .config, zgodnie z ich skonfigurowania, dostarczane przez system powiązanie takich jak `NetTcpBinding` lub niestandardowego powiązania za pomocą `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="aec2a-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="aec2a-105">Podczas zapisu w niestandardowym kanale i je ujawnić w modelu programowania przy użyciu nowego `BindingElement` lub `Binding`, należy utworzyć zestaw klas, aby `BindingElement` lub `Binding` można skonfigurować za pomocą pliku .config.</span><span class="sxs-lookup"><span data-stu-id="aec2a-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="aec2a-106">Narzędzie ConfigurationCodeGenerator do wygenerowania tych klas i udoskonalenie procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="aec2a-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="aec2a-107">Aby utworzyć narzędzie</span><span class="sxs-lookup"><span data-stu-id="aec2a-107">To build the tool</span></span>  
  
1.  <span data-ttu-id="aec2a-108">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aec2a-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="aec2a-109">Tworzenie rozwiązania generuje jeden plik: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="aec2a-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="aec2a-110">Plik SampleRun.cmd zawiera przykładowy wiersz polecenia, który przedstawia sposób użycia to narzędzie do generowania klasy dla [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="aec2a-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="aec2a-111">Aby uruchomić narzędzie</span><span class="sxs-lookup"><span data-stu-id="aec2a-111">To run the tool</span></span>  
  
1.  <span data-ttu-id="aec2a-112">W wierszu polecenia wpisz następujące, jeżeli masz zarówno niestandardowego `BindingElement` typu i niestandardowej `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="aec2a-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="aec2a-113">Lub wpisz następujące polecenie, jeśli masz tylko niestandardowego `BindingElement` typu:</span><span class="sxs-lookup"><span data-stu-id="aec2a-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="aec2a-114">Lub wpisz następujące polecenie, jeśli masz tylko niestandardowego `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="aec2a-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="aec2a-115">Polecenie generuje trzy pliki .cs dla `BindingElement` (Jeśli określono /: opcja), pięć plików .cs standardu `Binding` (Jeśli określono /sb: opcja) i pliku XML.</span><span class="sxs-lookup"><span data-stu-id="aec2a-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1.  <span data-ttu-id="aec2a-116">Jeśli użyto opcji /be jedną .cs plików implementuje `BindingElementExtensionSection` Twojego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="aec2a-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="aec2a-117">Ten kod przedstawia Twojej `BindingElement` do konfiguracji systemu, aby powiązania niestandardowe można użyć z elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="aec2a-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="aec2a-118">Inne pliki mają klasy reprezentujące domyślne i stałe.</span><span class="sxs-lookup"><span data-stu-id="aec2a-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="aec2a-119">Pliki mają `//TODO` komentarze do odnotowania można zaktualizować wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="aec2a-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2.  <span data-ttu-id="aec2a-120">Jeśli określono opcję /sb zaimplementować dwa pliki .cs `StandardBindingElement` i `StandardBindingCollectionElement` odpowiednio, który udostępnia standardowe wiązania do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="aec2a-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="aec2a-121">Inne pliki mają klasy reprezentujące domyślne i stałe.</span><span class="sxs-lookup"><span data-stu-id="aec2a-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="aec2a-122">Pliki mają `//TODO` komentarze do odnotowania można zaktualizować wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="aec2a-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="aec2a-123">Jeśli określono /sb: opcja CodeToAddTo\<*YourStdBinding*> .cs zawiera kod, który należy ręcznie dodać do klasy, który implementuje standardowe wiązania.</span><span class="sxs-lookup"><span data-stu-id="aec2a-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="aec2a-124">Plik SampleConfig.xml zawiera kod konfiguracji, które należy dodać do pliku konfiguracji, który rejestruje programy obsługi zdefiniowane w poprzednim kroku, 1 lub 2.</span><span class="sxs-lookup"><span data-stu-id="aec2a-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec2a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aec2a-125">See Also</span></span>
