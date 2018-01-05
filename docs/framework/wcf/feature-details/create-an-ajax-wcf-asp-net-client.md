---
title: "Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafa15129e4a131c5f50eb3296a87fc141e1bda6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi
W tym temacie przedstawiono sposób użycia programu Visual Studio 2008, można utworzyć z włączoną obsługą technologii AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi i kliencie programu ASP.NET, który uzyskuje dostęp do usługi. Kod dla usługi i dla klienta znajdują się w sekcji przykład po procedury ich tworzenia są opisane w sekcji procedur.  
  
### <a name="to-create-the-aspnet-client-application"></a>Aby utworzyć aplikację klienta ASP.NET  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Z **pliku** menu, wybierz opcję **nowy**, następnie **projektu**, następnie **sieci Web**, a następnie wybierz **aplikacji sieci Web ASP.NET**.  
  
3.  Nazwij projekt `SandwichServices` i kliknij przycisk **OK**.  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>Aby utworzyć usługę WCF interfejsu AJAX  
  
1.  Kliknij prawym przyciskiem myszy `SandwichServices` projektu w **Eksploratora rozwiązań** i zaznacz **Dodaj**, następnie **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX** .  
  
2.  Nazwa usługi `CostService` w **nazwa** polu i kliknij przycisk **Dodaj**.  
  
3.  Otwórz plik CostService.svc.cs.  
  
4.  Określ `Namespace` dla <xref:System.ServiceModel.ServiceContractAttribute> jako `SandwichService`:  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  Implementuje operacji w usłudze. Dodaj <xref:System.ServiceModel.OperationContractAttribute> do każdej operacji, aby wskazać, że są one częścią umowy. Poniższy przykład implementuje metodę, która zwraca koszt określonej ilości kanapki.  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a>Aby skonfigurować klienta do uzyskania dostępu do usługi  
  
1.  Otwórz stronę Default.aspx i wybierz **projekt** widoku.  
  
2.  Z **widoku** menu, wybierz opcję **przybornika**.  
  
3.  Rozwiń węzeł **rozszerzenia AJAX** węzła i przeciąganie i upuszczanie **ScriptManager** na stronie Default.aspx.  
  
4.  Kliknij prawym przyciskiem myszy **ScriptManager** i wybierz **właściwości**.  
  
5.  Rozwiń węzeł **usług** kolekcji w **właściwości** okno, aby otworzyć **edytora kolekcji servicereference kierowany** okna.  
  
6.  Kliknij przycisk **Dodaj**, określ `CostService.svc` jako **ścieżki** odwołania, a następnie kliknij przycisk **OK**.  
  
7.  Rozwiń węzeł **HTML** w węźle **przybornika** i przeciągnij i upuść **danych wejściowych (przycisk)** na stronie Default.aspx.  
  
8.  Kliknij prawym przyciskiem myszy **przycisk** i wybierz **właściwości**.  
  
9. Zmień **wartość** do `Price for 3 Sandwiches`.  
  
10. Kliknij dwukrotnie **przycisk** dostęp do kodu JavaScript.  
  
11. Przekaż następujący kod JavaScript w <`script`> elementu.  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>Aby uzyskać dostęp do usługi z klienta  
  
1.  Użyj klawiszy Ctrl + F5, aby uruchomić usługę i klienta sieci Web. Kliknij przycisk **cena 3 kanapki Grilled** przycisk, aby wygenerować oczekiwane dane wyjściowe "3,75".  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zawiera kod usługi zawarte w pliku WCFService.svc.cs i zawarte w pliku Default.aspx kod klienta.  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
```     
