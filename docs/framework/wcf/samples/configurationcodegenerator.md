---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990068"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="1113f-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="1113f-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="1113f-103">ConfigurationCodeGenerator to narzędzie, za pomocą którego można uwidocznić niestandardowe implementacje kanałów w systemie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1113f-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="1113f-104">Umożliwia to użytkownikom niestandardowego kanału Konfigurowanie kanału przy użyciu pliku. config tak samo jak w przypadku konfigurowania powiązania dostarczonego przez system, takiego jak `NetTcpBinding` lub niestandardowego powiązania `TcpTransportBindingElement`przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="1113f-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="1113f-105">Podczas pisania niestandardowego kanału i uwidocznienia go w modelu programowania przy użyciu `BindingElement` nowego lub `Binding`, należy utworzyć zestaw `Binding` klas, aby można było `BindingElement` użyć pliku. config.</span><span class="sxs-lookup"><span data-stu-id="1113f-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="1113f-106">Możesz użyć narzędzia ConfigurationCodeGenerator do wygenerowania tych klas i zwiększenia środowiska klienta.</span><span class="sxs-lookup"><span data-stu-id="1113f-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="1113f-107">Aby skompilować narzędzie</span><span class="sxs-lookup"><span data-stu-id="1113f-107">To build the tool</span></span>  
  
1. <span data-ttu-id="1113f-108">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1113f-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="1113f-109">Kompilowanie rozwiązania generuje jeden plik: ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="1113f-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="1113f-110">Plik SampleRun. cmd zawiera przykładowy wiersz polecenia, który pokazuje, jak używać tego narzędzia do generowania klas do [transportu: Przykład](../../../../docs/framework/wcf/samples/transport-udp.md) protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="1113f-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="1113f-111">Aby uruchomić narzędzie</span><span class="sxs-lookup"><span data-stu-id="1113f-111">To run the tool</span></span>  
  
1. <span data-ttu-id="1113f-112">W wierszu polecenia wpisz następujące polecenie, jeśli istnieje zarówno typ niestandardowy `BindingElement` , jak i typ niestandardowy: `Binding`</span><span class="sxs-lookup"><span data-stu-id="1113f-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="1113f-113">Lub wpisz następujące, jeśli masz tylko typ niestandardowy `BindingElement` :</span><span class="sxs-lookup"><span data-stu-id="1113f-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="1113f-114">Lub wpisz następujące, jeśli masz tylko typ niestandardowy `Binding` :</span><span class="sxs-lookup"><span data-stu-id="1113f-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="1113f-115">Polecenie generuje trzy pliki. cs dla `BindingElement` (Jeśli określono/be: opcja), pięć plików CS dla standardowego `Binding` (Jeśli określono/SB: Option) i plik. XML.</span><span class="sxs-lookup"><span data-stu-id="1113f-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="1113f-116">Jeśli użyto opcji/BE, jeden z plików CS implementuje `BindingElementExtensionSection` dla elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="1113f-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="1113f-117">Ten kod uwidacznia `BindingElement` systemowi konfiguracji, tak aby inne powiązania niestandardowe mogły korzystać z elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="1113f-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="1113f-118">Inne pliki zawierają klasy, które reprezentują wartości domyślne i stałe.</span><span class="sxs-lookup"><span data-stu-id="1113f-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="1113f-119">Pliki mają `//TODO` komentarze, aby przypominać o zaktualizowaniu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="1113f-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="1113f-120">W przypadku wybrania opcji/SB dwa z plików CS implementują `StandardBindingElement` `StandardBindingCollectionElement` i odpowiednio, które udostępniają standardowe powiązanie z systemem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1113f-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="1113f-121">Inne pliki zawierają klasy, które reprezentują wartości domyślne i stałe.</span><span class="sxs-lookup"><span data-stu-id="1113f-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="1113f-122">Pliki mają `//TODO` komentarze, aby przypominać o zaktualizowaniu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="1113f-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="1113f-123">W przypadku określenia opcji/SB: CodeToAddTo\<*YourStdBinding*>. cs ma kod, który trzeba ręcznie dodać do klasy, która implementuje powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="1113f-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="1113f-124">Plik SampleConfig. xml zawiera kod konfiguracji, który należy dodać do pliku konfiguracji, który rejestruje programy obsługi zdefiniowane w poprzednim kroku 1 lub 2.</span><span class="sxs-lookup"><span data-stu-id="1113f-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
