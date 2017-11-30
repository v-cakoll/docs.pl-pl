---
title: "Wskazówki - uzyskiwanie dostępu do usługi sieci Web za pomocą dostawców typów (F #)"
description: "Dowiedz się, jak użyć dostawcy typu Web Services Description Language (WSDL) dostępne w F # 3.0 w celu uzyskania dostępu do usługi WSDL."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="9d886-104">Wskazówki: uzyskiwanie dostępu do usługi sieci Web za pomocą dostawców typów</span><span class="sxs-lookup"><span data-stu-id="9d886-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="9d886-105">Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="9d886-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="9d886-106">Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.</span><span class="sxs-lookup"><span data-stu-id="9d886-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="9d886-107">Linki odwołań interfejsu API spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="9d886-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="9d886-108">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="9d886-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="9d886-109">Ten przewodnik przedstawia sposób użycia dostawcy typu Web Services Description Language (WSDL), który jest dostępny w F # 3.0 w celu uzyskiwania dostępu do usługi WSDL.</span><span class="sxs-lookup"><span data-stu-id="9d886-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="9d886-110">W innych językach .NET generowania kodu do uzyskania dostępu do usługi sieci web przez wywołanie svcutil.exe lub przez dodanie odwołania sieci web w na przykład C# projektu Visual Studio, aby wywołać svcutil.exe można uzyskać.</span><span class="sxs-lookup"><span data-stu-id="9d886-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="9d886-111">W języku F # istnieje dodatkowa opcja przy użyciu dostawcy typów WSDL, dlatego tak szybko, jak można napisać kod, który tworzy wsdlservice — typ, typy były generowane i stają się dostępne.</span><span class="sxs-lookup"><span data-stu-id="9d886-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="9d886-112">Ten proces zależy od usługi są dostępne podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="9d886-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="9d886-113">W tym przewodniku przedstawiono następujące zadania.</span><span class="sxs-lookup"><span data-stu-id="9d886-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="9d886-114">W tej kolejności dla wskazówki została wykonana pomyślnie, należy wykonać je:</span><span class="sxs-lookup"><span data-stu-id="9d886-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="9d886-115">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="9d886-115">Creating the project</span></span>
<br />

- <span data-ttu-id="9d886-116">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="9d886-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="9d886-117">Wywołanie usługi sieci web i przetwarzania wyników</span><span class="sxs-lookup"><span data-stu-id="9d886-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="9d886-118">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="9d886-118">Creating the project</span></span>
<span data-ttu-id="9d886-119">W kroku utworzenie projektu i dodać odpowiednie odwołań do używania dostawcy typów WSDL.</span><span class="sxs-lookup"><span data-stu-id="9d886-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="9d886-120">Aby utworzyć i skonfigurować projekt języka F#</span><span class="sxs-lookup"><span data-stu-id="9d886-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="9d886-121">Otwórz nowy projekt aplikacji konsoli F #.</span><span class="sxs-lookup"><span data-stu-id="9d886-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="9d886-122">W **Eksploratora rozwiązań**, otwórz menu skrótów projektu **odwołania** węzeł, a następnie wybierz pozycję **Dodaj odwołanie do**.</span><span class="sxs-lookup"><span data-stu-id="9d886-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="9d886-123">W **zestawy** obszarze, wybierz **Framework**, a następnie na liście dostępnych zestawów, wybierz **System.Runtime.Serialization** i  **System.ServiceModel**.</span><span class="sxs-lookup"><span data-stu-id="9d886-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="9d886-124">W **zestawy** obszarze, wybierz **rozszerzenia**.</span><span class="sxs-lookup"><span data-stu-id="9d886-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="9d886-125">Na liście dostępnych zestawów, wybierz **FSharp.Data.TypeProviders**, a następnie wybierz pozycję **OK** przycisk, aby dodać odwołania do tych zestawów.</span><span class="sxs-lookup"><span data-stu-id="9d886-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="9d886-126">Konfigurowanie dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="9d886-126">Configuring the type provider</span></span>
<span data-ttu-id="9d886-127">W tym kroku dostawca typu WSDL jest służy do generowania typów TerraServer usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="9d886-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="9d886-128">Aby skonfigurować dostawcę typów i wygenerować typy</span><span class="sxs-lookup"><span data-stu-id="9d886-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="9d886-129">Dodaj następujący wiersz kodu, aby otworzyć przestrzeni nazw typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="9d886-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="9d886-130">Dodaj następujący wiersz kodu do wywołania typ dostawcy z usługą sieci web.</span><span class="sxs-lookup"><span data-stu-id="9d886-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="9d886-131">W tym przykładzie jest używana usługa sieci web TerraServer.</span><span class="sxs-lookup"><span data-stu-id="9d886-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="9d886-132">Jeśli identyfikator URI usługi jest nieprawidłowo zapisana lub jeśli sama usługa nie działa lub nie wykonuje czerwona falista zostanie ten wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="9d886-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="9d886-133">Po wskazaniu kod komunikat o błędzie w tym artykule opisano problem.</span><span class="sxs-lookup"><span data-stu-id="9d886-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="9d886-134">Można znaleźć w tych samych informacji **listy błędów** okna lub **okno danych wyjściowych** po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="9d886-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="9d886-135">Istnieją dwa sposoby, aby określić ustawienia konfiguracji dla połączenia WSDL, przy użyciu pliku app.config projektu lub za pomocą parametrów statycznych typu w deklaracji typu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="9d886-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="9d886-136">Svcutil.exe służy do generowania elementy pliku odpowiednia konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="9d886-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="9d886-137">Aby uzyskać więcej informacji o używaniu svcutil.exe do generowania informacji o konfiguracji dla usługi sieci web, zobacz [narzędzie do obsługi metadanych elementu ServiceModel &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="9d886-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="9d886-138">Pełny opis parametrów statycznych typu dostawcy typów WSDL, zobacz [wsdlservice — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="9d886-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="9d886-139">Wywołanie usługi sieci web i przetwarzania wyników</span><span class="sxs-lookup"><span data-stu-id="9d886-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="9d886-140">Każda usługa sieci web ma swój własny zestaw typów, które są używane jako parametry dla swojego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="9d886-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="9d886-141">W tym kroku przygotowanie tych parametrów, wywołania metody sieci web i przetwarza zwraca informacje.</span><span class="sxs-lookup"><span data-stu-id="9d886-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="9d886-142">Aby wywołać usługę sieci web i przetworzyć wyników</span><span class="sxs-lookup"><span data-stu-id="9d886-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="9d886-143">Usługa sieci web może limitu czasu lub przestaną działać, dlatego wywołania usługi sieci web, należy uwzględnić w obsługi bloku wyjątków.</span><span class="sxs-lookup"><span data-stu-id="9d886-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="9d886-144">Wpisz następujący kod, aby uzyskać dane z usługi sieci web.</span><span class="sxs-lookup"><span data-stu-id="9d886-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="9d886-145">Zwróć uwagę, aby utworzyć typy danych, które są wymagane przez usługę sieci web, takich jak **miejsce** i **lokalizacji**, ponieważ typy zagnieżdżone w obszarze wsdlservice — typ **TerraService**.</span><span class="sxs-lookup"><span data-stu-id="9d886-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="9d886-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d886-146">See Also</span></span>
[<span data-ttu-id="9d886-147">Wsdlservice — dostawca typów</span><span class="sxs-lookup"><span data-stu-id="9d886-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="9d886-148">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="9d886-148">Type Providers</span></span>](index.md)
