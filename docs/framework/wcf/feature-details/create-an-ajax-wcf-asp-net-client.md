---
title: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET w programie Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: a6d6e87de6200a5cb9bba566d595066673cdf9cf
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834786"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi

W tym temacie przedstawiono sposób użycia programu Visual Studio do utworzenia usługi Windows Communication Foundation (WCF) z włączoną obsługą technologii AJAX i klienta ASP.NET, który uzyskuje dostęp do usługi.

## <a name="create-an-aspnet-web-app"></a>Tworzenie aplikacji sieci Web ASP.NET

1. Otwórz program Visual Studio.

1. Z menu **plik** wybierz pozycję **Nowy** > **projekt**

1. W oknie dialogowym **Nowy projekt** rozwiń kategorię **zainstalowaną**@no__t-**2 C#Visual**  >  dla**sieci Web** , a następnie wybierz pozycję **aplikacja sieci Web ASP.NET (.NET Framework)** .

1. Nadaj projektowi nazwę **SandwichServices** i kliknij przycisk **OK**.

1. W oknie dialogowym **Nowa aplikacja sieci Web ASP.NET** wybierz opcję **pusty** , a następnie wybierz przycisk **OK**.

   ![Okno dialogowe typu aplikacji sieci Web ASP.NET w programie Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Dodawanie formularza sieci Web

1. Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** rozwiń kategorię **zainstalowaną**@no__t-**2 C#Visual**  >  dla**sieci Web** , a następnie wybierz szablon **formularza sieci Web** .

1. Zaakceptuj nazwę domyślną (**WebForm1**), a następnie wybierz pozycję **Dodaj**.

   W widoku **źródła** zostanie otwarty *formularz WebForm1. aspx* .

1. Dodaj następujący znacznik wewnątrz tagów **@no__t 1body >** :

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>Tworzenie usługi WCF z włączoną obsługą technologii AJAX

1. Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **nowy element**.

1. W oknie dialogowym **Dodaj nowy element** rozwiń kategorię **zainstalowaną**@no__t-**2 C#Visual**  >  dla**sieci Web** , a następnie wybierz szablon **usługi WCF (z włączoną obsługą technologii AJAX)** .

   ![Szablon elementu usługi WCF (z obsługą technologii AJAX) w programie Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Nazwij usługę **CostService** , a następnie wybierz pozycję **Dodaj**.

   *CostService.svc.cs* zostanie otwarty w edytorze.

1. Implementowanie operacji w usłudze. Dodaj następującą metodę do klasy CostService, aby obliczyć koszt ilości Sandwiches:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Konfigurowanie klienta do uzyskiwania dostępu do usługi

1. Otwórz plik *WebForm1. aspx* i wybierz widok **projekt** .

2. Z menu **Widok** wybierz pozycję **Przybornik**.

3. Rozwiń węzeł **rozszerzenia AJAX** i przeciągnij i upuść element **ScriptManager** do formularza.

4. W widoku **źródła** Dodaj następujący kod między tagami **\<ScriptManager >** , aby określić ścieżkę do usługi WCF:

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. Dodaj kod dla funkcji JavaScript `Calculate()`. Umieść poniższy kod w sekcji **nagłówka** formularza sieci Web:

    ```html
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

   Ten kod wywołuje metodę CostService w celu obliczenia ceny dla trzech Sandwiches, a następnie wyświetla wynik w zakresie o nazwie **additionResult**.

## <a name="run-the-program"></a>Uruchom program

Upewnij się, że *WebForm1. aspx* ma fokus, a następnie naciśnij przycisk **Start** , aby uruchomić klienta sieci Web. Przycisk ma zielony trójkąt i przypomina **IIS Express (Microsoft Edge)** . Możesz też nacisnąć klawisz <kbd>F5</kbd>. Kliknij przycisk **Cena 3 Sandwiches** , aby wygenerować oczekiwane dane wyjściowe "3,75".

## <a name="example"></a>Przykład

Poniżej znajduje się pełny kod w pliku *CostService.svc.cs* :

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

Poniżej znajduje się pełna zawartość strony *WebForm1. aspx* :

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
