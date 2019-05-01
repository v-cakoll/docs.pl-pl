---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 97197926db0b44f1ad36e2eba6ab6bec42eced33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943926"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="56c5b-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="56c5b-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="56c5b-103">ConfigurationCodeGenerator jest narzędziem, które można użyć do udostępnienia implementacji usługi niestandardowym kanale w celu system konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="56c5b-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="56c5b-104">Dzięki temu użytkownicy niestandardowy kanał skonfigurować kanał przy użyciu pliku config, zgodnie z ich konfigurowania, dostarczane przez system powiązań takich jak `NetTcpBinding` lub niestandardowego powiązania za pomocą `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="56c5b-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="56c5b-105">Podczas zapisu w niestandardowym kanale i udostępnić ją modelu programowania przy użyciu nowego `BindingElement` lub `Binding`, należy utworzyć zestaw klas, które umożliwiają `BindingElement` lub `Binding` można konfigurować przy użyciu pliku Config.</span><span class="sxs-lookup"><span data-stu-id="56c5b-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="56c5b-106">Narzędzie ConfigurationCodeGenerator do wygenerowania tych klas i poprawić funkcjonalność z perspektywy klienta.</span><span class="sxs-lookup"><span data-stu-id="56c5b-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="56c5b-107">Aby utworzyć narzędzie</span><span class="sxs-lookup"><span data-stu-id="56c5b-107">To build the tool</span></span>  
  
1. <span data-ttu-id="56c5b-108">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="56c5b-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="56c5b-109">Skompilować rozwiązanie generuje jeden plik: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="56c5b-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="56c5b-110">Plik SampleRun.cmd zawiera przykładowy wiersz polecenia, który pokazuje, jak używać tego narzędzia do generowania klasy dla [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="56c5b-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="56c5b-111">Aby uruchomić narzędzie</span><span class="sxs-lookup"><span data-stu-id="56c5b-111">To run the tool</span></span>  
  
1. <span data-ttu-id="56c5b-112">W wierszu polecenia wpisz następujące polecenie, w przypadku obu niestandardowe `BindingElement` typu i niestandardowego `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="56c5b-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="56c5b-113">Lub wpisz następujące polecenie, jeśli masz tylko niestandardowego `BindingElement` typu:</span><span class="sxs-lookup"><span data-stu-id="56c5b-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="56c5b-114">Lub wpisz następujące polecenie, jeśli masz tylko niestandardowego `Binding` typu:</span><span class="sxs-lookup"><span data-stu-id="56c5b-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="56c5b-115">Polecenie spowoduje wygenerowanie trzy pliki CS `BindingElement` (Jeśli określono / to: opcja), pięć plików .cs standardu `Binding` (Jeśli określono /sb: opcja) i pliku XML.</span><span class="sxs-lookup"><span data-stu-id="56c5b-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="56c5b-116">Jeśli użyto opcji /be jeden .cs pliki implementuje `BindingElementExtensionSection` dla danego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="56c5b-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="56c5b-117">Ten kod przedstawia swoje `BindingElement` do konfiguracji systemu, aby powiązań niestandardowych można użyć usługi elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="56c5b-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="56c5b-118">Inne pliki mają klas, które reprezentują stałe i wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="56c5b-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="56c5b-119">Pliki mają `//TODO` komentarze, aby przypomnieć Ci można zaktualizować wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="56c5b-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="56c5b-120">Jeśli określono opcję /sb dwa pliki CS zaimplementować `StandardBindingElement` i `StandardBindingCollectionElement` odpowiednio, który udostępnia standardowy wiązania do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="56c5b-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="56c5b-121">Inne pliki mają klas, które reprezentują stałe i wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="56c5b-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="56c5b-122">Pliki mają `//TODO` komentarze, aby przypomnieć Ci można zaktualizować wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="56c5b-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="56c5b-123">Jeśli określono /sb: opcja CodeToAddTo\<*YourStdBinding*> .cs zawiera kod, należy ręcznie dodać do klasy, która implementuje standardowe wiązania.</span><span class="sxs-lookup"><span data-stu-id="56c5b-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="56c5b-124">Plik SampleConfig.xml zawiera kod konfiguracji, które należy dodać do pliku konfiguracji, który rejestruje programy obsługi zdefiniowane w poprzednim kroku, 1 lub 2.</span><span class="sxs-lookup"><span data-stu-id="56c5b-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
