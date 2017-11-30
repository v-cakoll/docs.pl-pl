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
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>Wskazówki: uzyskiwanie dostępu do usługi sieci Web za pomocą dostawców typów

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

> [!NOTE]
Linki odwołań interfejsu API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Ten przewodnik przedstawia sposób użycia dostawcy typu Web Services Description Language (WSDL), który jest dostępny w F # 3.0 w celu uzyskiwania dostępu do usługi WSDL. W innych językach .NET generowania kodu do uzyskania dostępu do usługi sieci web przez wywołanie svcutil.exe lub przez dodanie odwołania sieci web w na przykład C# projektu Visual Studio, aby wywołać svcutil.exe można uzyskać. W języku F # istnieje dodatkowa opcja przy użyciu dostawcy typów WSDL, dlatego tak szybko, jak można napisać kod, który tworzy wsdlservice — typ, typy były generowane i stają się dostępne. Ten proces zależy od usługi są dostępne podczas pisania kodu.

W tym przewodniku przedstawiono następujące zadania. W tej kolejności dla wskazówki została wykonana pomyślnie, należy wykonać je:


- Tworzenie projektu
<br />

- Konfigurowanie dostawcy typów
<br />

- Wywołanie usługi sieci web i przetwarzania wyników
<br />


## <a name="creating-the-project"></a>Tworzenie projektu
W kroku utworzenie projektu i dodać odpowiednie odwołań do używania dostawcy typów WSDL.


#### <a name="to-create-and-set-up-an-f-project"></a>Aby utworzyć i skonfigurować projekt języka F#

1. Otwórz nowy projekt aplikacji konsoli F #.
<br />

2. W **Eksploratora rozwiązań**, otwórz menu skrótów projektu **odwołania** węzeł, a następnie wybierz pozycję **Dodaj odwołanie do**.
<br />

3. W **zestawy** obszarze, wybierz **Framework**, a następnie na liście dostępnych zestawów, wybierz **System.Runtime.Serialization** i  **System.ServiceModel**.
<br />

4. W **zestawy** obszarze, wybierz **rozszerzenia**.
<br />

5. Na liście dostępnych zestawów, wybierz **FSharp.Data.TypeProviders**, a następnie wybierz pozycję **OK** przycisk, aby dodać odwołania do tych zestawów.
<br />

## <a name="configuring-the-type-provider"></a>Konfigurowanie dostawcy typów
W tym kroku dostawca typu WSDL jest służy do generowania typów TerraServer usługi sieci web.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Aby skonfigurować dostawcę typów i wygenerować typy

1. Dodaj następujący wiersz kodu, aby otworzyć przestrzeni nazw typu dostawcy.
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. Dodaj następujący wiersz kodu do wywołania typ dostawcy z usługą sieci web. W tym przykładzie jest używana usługa sieci web TerraServer.
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  Jeśli identyfikator URI usługi jest nieprawidłowo zapisana lub jeśli sama usługa nie działa lub nie wykonuje czerwona falista zostanie ten wiersz kodu. Po wskazaniu kod komunikat o błędzie w tym artykule opisano problem. Można znaleźć w tych samych informacji **listy błędów** okna lub **okno danych wyjściowych** po utworzeniu.
<br />  Istnieją dwa sposoby, aby określić ustawienia konfiguracji dla połączenia WSDL, przy użyciu pliku app.config projektu lub za pomocą parametrów statycznych typu w deklaracji typu dostawcy. Svcutil.exe służy do generowania elementy pliku odpowiednia konfiguracja. Aby uzyskać więcej informacji o używaniu svcutil.exe do generowania informacji o konfiguracji dla usługi sieci web, zobacz [narzędzie do obsługi metadanych elementu ServiceModel &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx). Pełny opis parametrów statycznych typu dostawcy typów WSDL, zobacz [wsdlservice — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>Wywołanie usługi sieci web i przetwarzania wyników
Każda usługa sieci web ma swój własny zestaw typów, które są używane jako parametry dla swojego wywołania metody. W tym kroku przygotowanie tych parametrów, wywołania metody sieci web i przetwarza zwraca informacje.


#### <a name="to-call-the-web-service-and-process-the-results"></a>Aby wywołać usługę sieci web i przetworzyć wyników

1. Usługa sieci web może limitu czasu lub przestaną działać, dlatego wywołania usługi sieci web, należy uwzględnić w obsługi bloku wyjątków. Wpisz następujący kod, aby uzyskać dane z usługi sieci web.
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

Zwróć uwagę, aby utworzyć typy danych, które są wymagane przez usługę sieci web, takich jak **miejsce** i **lokalizacji**, ponieważ typy zagnieżdżone w obszarze wsdlservice — typ **TerraService**.
<br />


## <a name="see-also"></a>Zobacz też
[Wsdlservice — dostawca typów](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[Dostawcy typów](index.md)
