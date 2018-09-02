---
title: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET w programie Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 07a1e903991e09243572f2a99c19edae7f9793b6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384289"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi

W tym temacie pokazano, jak używać programu Visual Studio do tworzenia usługi z włączoną obsługą technologii AJAX Windows Communication Foundation (WCF) i kliencie programu ASP.NET, który uzyskuje dostęp do usługi.

## <a name="create-an-aspnet-web-app"></a>Tworzenie aplikacji sieci web ASP.NET

1. Otwórz program Visual Studio.

1. Z **pliku** menu, wybierz opcję **New** > **projektu**

1. W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** > **Web** kategorii, a następnie Wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)**.

1. Nadaj projektowi nazwę **SandwichServices** i kliknij przycisk **OK**.

1. W **Nowa aplikacja internetowa ASP.NET** okno dialogowe, wybierz opcję **pusty** , a następnie wybierz **OK**.

   ![Okno dialogowe typu aplikacji sieci web platformy ASP.NET w programie Visual Studio](../media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Dodaj formularz sieci web

1. Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** > **Web** kategorii, a następnie Wybierz **formularz sieci Web** szablonu.

1. Zaakceptuj nazwę domyślną (**WebForm1**), a następnie wybierz pozycję **Dodaj**.

   *WebForm1.aspx* zostanie otwarty w **źródła** widoku.

1. Dodaj następujący kod wewnątrz  **\<treści >** tagi:

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>Tworzenie usługi WCF z włączoną obsługą technologii AJAX

1. Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** > **Web** kategorii, a następnie Wybierz **usługi WCF (włączoną obsługą technologii AJAX)** szablonu.

   ![Szablon elementu (włączoną obsługą technologii AJAX) usługi WCF w programie Visual Studio](../media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Nazwij usługę **CostService** , a następnie wybierz **Dodaj**.

   *CostService.svc.cs* zostanie otwarty w edytorze.

1. Implementowanie operacji w usłudze. Dodaj następującą metodę do klasy CostService, aby obliczyć koszt ilość kanapki:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Konfigurowanie klienta do uzyskania dostępu do usługi

1. Otwórz *WebForm1.aspx* plik i wybierz **projektowania** widoku.

2. Z **widoku** menu, wybierz opcję **przybornika**.

3. Rozwiń **rozszerzenia AJAX** węzła i przeciągania i upuszczania **ScriptManager** na formularz.

4. Ponownie **źródła** wyświetlanie, Dodaj następujący kod między  **\<ScriptManager >** tagów, aby określić ścieżkę do usługi WCF:

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. Dodaj kod dla funkcji języka Javascript `Calculate()`. Umieść następujący kod w **head** części formularza sieci web:

    ```javascript
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   Ten kod wywołuje metodę CostService do obliczania ceny dla trzech kanapki, a następnie wyświetla wynik w zakresie o nazwie **additionResult**.

## <a name="run-the-program"></a>Uruchom program

Upewnij się, że *WebForm1.aspx* ma fokus, a następnie naciśnij klawisz **Start** przycisk, aby uruchomić klienta sieci web. Ten przycisk ma zielony trójkąt i jest wyświetlany komunikat podobny do **usług IIS Express (Microsoft Edge)**. Lub możesz nacisnąć przycisk **F5**. Kliknij przycisk **cena 3 kanapki** przycisk, aby wygenerować oczekiwane dane wyjściowe "3,75".

## <a name="example-code"></a>Przykładowy kod

Oto pełny kod w *CostService.svc.cs* pliku:

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

Poniżej znajduje się pełna zawartość *WebForm1.aspx* strony:

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
