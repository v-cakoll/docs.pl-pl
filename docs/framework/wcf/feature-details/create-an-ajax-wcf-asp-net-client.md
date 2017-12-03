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
ms.openlocfilehash: b136565730c1b3175abff8b057a69acc6609a44d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="1dfb4-102">Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi</span><span class="sxs-lookup"><span data-stu-id="1dfb4-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>
<span data-ttu-id="1dfb4-103">W tym temacie przedstawiono sposób użycia programu Visual Studio 2008, można utworzyć z włączoną obsługą technologii AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi i kliencie programu ASP.NET, który uzyskuje dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-103">This topic shows how to use Visual Studio 2008 to create an AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and an ASP.NET client that accesses the service.</span></span> <span data-ttu-id="1dfb4-104">Kod dla usługi i dla klienta znajdują się w sekcji przykład po procedury ich tworzenia są opisane w sekcji procedur.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-104">The code for the service and for the client are provided in the Example section after the steps for creating them are described in the Procedures section.</span></span>  
  
### <a name="to-create-the-aspnet-client-application"></a><span data-ttu-id="1dfb4-105">Aby utworzyć aplikację klienta ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1dfb4-105">To create the ASP.NET client application</span></span>  
  
1.  <span data-ttu-id="1dfb4-106">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1dfb4-106">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="1dfb4-107">Z **pliku** menu, wybierz opcję **nowy**, następnie **projektu**, następnie **sieci Web**, a następnie wybierz **aplikacji sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-107">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Application**.</span></span>  
  
3.  <span data-ttu-id="1dfb4-108">Nazwij projekt `SandwichServices` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-108">Name the Project `SandwichServices` and click **OK**.</span></span>  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a><span data-ttu-id="1dfb4-109">Aby utworzyć usługę WCF interfejsu AJAX</span><span class="sxs-lookup"><span data-stu-id="1dfb4-109">To create the WCF AJAX-enabled service</span></span>  
  
1.  <span data-ttu-id="1dfb4-110">Kliknij prawym przyciskiem myszy `SandwichServices` projektu w **Eksploratora rozwiązań** i zaznacz **Dodaj**, następnie **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX** .</span><span class="sxs-lookup"><span data-stu-id="1dfb4-110">Right-click the `SandwichServices` project in the **Solution Explorer** window and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="1dfb4-111">Nazwa usługi `CostService` w **nazwa** polu i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-111">Name the service `CostService` in the **Name** box and click **Add**.</span></span>  
  
3.  <span data-ttu-id="1dfb4-112">Otwórz plik CostService.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-112">Open the CostService.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="1dfb4-113">Określ `Namespace` dla <xref:System.ServiceModel.ServiceContractAttribute> jako `SandwichService`:</span><span class="sxs-lookup"><span data-stu-id="1dfb4-113">Specify the `Namespace` for <xref:System.ServiceModel.ServiceContractAttribute> as `SandwichService`:</span></span>  
  
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
  
5.  <span data-ttu-id="1dfb4-114">Implementuje operacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-114">Implement the operations in the service.</span></span> <span data-ttu-id="1dfb4-115">Dodaj <xref:System.ServiceModel.OperationContractAttribute> do każdej operacji, aby wskazać, że są one częścią umowy.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-115">Add the <xref:System.ServiceModel.OperationContractAttribute> to each of the operations to indicate that they are part of the contract.</span></span> <span data-ttu-id="1dfb4-116">Poniższy przykład implementuje metodę, która zwraca koszt określonej ilości kanapki.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-116">The following example implements a method that returns the cost of a given quantity of sandwiches.</span></span>  
  
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
  
### <a name="to-configure-the-client-to-access-the-service"></a><span data-ttu-id="1dfb4-117">Aby skonfigurować klienta do uzyskania dostępu do usługi</span><span class="sxs-lookup"><span data-stu-id="1dfb4-117">To configure the client to access the service</span></span>  
  
1.  <span data-ttu-id="1dfb4-118">Otwórz stronę Default.aspx i wybierz **projekt** widoku.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-118">Open the Default.aspx page and select the **Design** view.</span></span>  
  
2.  <span data-ttu-id="1dfb4-119">Z **widoku** menu, wybierz opcję **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-119">From the **View** menu, select **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="1dfb4-120">Rozwiń węzeł **rozszerzenia AJAX** węzła i przeciąganie i upuszczanie **ScriptManager** na stronie Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-120">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** on to the Default.aspx page.</span></span>  
  
4.  <span data-ttu-id="1dfb4-121">Kliknij prawym przyciskiem myszy **ScriptManager** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-121">Right-click the **ScriptManager** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="1dfb4-122">Rozwiń węzeł **usług** kolekcji w **właściwości** okno, aby otworzyć **edytora kolekcji servicereference kierowany** okna.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-122">Expand the **Services** collection in the **Properties** window to open up the **ServiceReference Collection Editor** window.</span></span>  
  
6.  <span data-ttu-id="1dfb4-123">Kliknij przycisk **Dodaj**, określ `CostService.svc` jako **ścieżki** odwołania, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-123">Click **Add**, specify `CostService.svc` as the **Path** referenced, and click **OK**.</span></span>  
  
7.  <span data-ttu-id="1dfb4-124">Rozwiń węzeł **HTML** w węźle **przybornika** i przeciągnij i upuść **danych wejściowych (przycisk)** na stronie Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-124">Expand the **HTML** node in the **Toolbox** and drag and drop an **Input (Button)** on to the Default.aspx page.</span></span>  
  
8.  <span data-ttu-id="1dfb4-125">Kliknij prawym przyciskiem myszy **przycisk** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-125">Right-click the **Button** and select **Properties**.</span></span>  
  
9. <span data-ttu-id="1dfb4-126">Zmień **wartość** do `Price for 3 Sandwiches`.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-126">Change the **Value** field to `Price for 3 Sandwiches`.</span></span>  
  
10. <span data-ttu-id="1dfb4-127">Kliknij dwukrotnie **przycisk** dostęp do kodu JavaScript.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-127">Double-click the **Button** to access the JavaScript code.</span></span>  
  
11. <span data-ttu-id="1dfb4-128">Przekaż następujący kod JavaScript w <`script`> elementu.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-128">Pass in the following JavaScript code within the <`script`> element.</span></span>  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a><span data-ttu-id="1dfb4-129">Aby uzyskać dostęp do usługi z klienta</span><span class="sxs-lookup"><span data-stu-id="1dfb4-129">To access the service from the client</span></span>  
  
1.  <span data-ttu-id="1dfb4-130">Użyj klawiszy Ctrl + F5, aby uruchomić usługę i klienta sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-130">Use Ctrl +F5 to launch the service and the Web client.</span></span> <span data-ttu-id="1dfb4-131">Kliknij przycisk **cena 3 kanapki Grilled** przycisk, aby wygenerować oczekiwane dane wyjściowe "3,75".</span><span class="sxs-lookup"><span data-stu-id="1dfb4-131">Click the **Price for 3 Grilled Sandwiches** button to generate the expected output of "3.75".</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfb4-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dfb4-132">Example</span></span>  
 <span data-ttu-id="1dfb4-133">W tym przykładzie zawiera kod usługi zawarte w pliku WCFService.svc.cs i zawarte w pliku Default.aspx kod klienta.</span><span class="sxs-lookup"><span data-stu-id="1dfb4-133">This example contains the service code contained in the WCFService.svc.cs file and the client code contained in the Default.aspx file.</span></span>  
  
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
