---
title: 'Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: c85ab6725876a2d523a18c817ce3fd89f0d2285a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184484"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF
Czasami deweloperzy muszą mieć pełną kontrolę nad tym, jak dane są zwracane z operacji usługi. Ma to miejsce, gdy operacja usługi musi zwracać dane w formacie nie obsługiwanym przez WCF. W tym temacie omówiono przy użyciu WCF WEB HTTP Model programowania do tworzenia takiej usługi. Ta usługa ma jedną operację, która zwraca strumień.  
  
### <a name="to-implement-the-service-contract"></a>Aby wdrożyć umowę serwisową  
  
1. Zdefiniuj umowę serwisową. Kontrakt jest `IImageServer` wywoływany i `GetImage` ma jedną <xref:System.IO.Stream>metodę o nazwie, która zwraca .  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Ponieważ metoda zwraca <xref:System.IO.Stream>, WCF zakłada, że operacja ma pełną kontrolę nad bajtami, które są zwracane z operacji usługi i nie stosuje formatowania do zwracanych danych.  
  
2. Zaimplementuj umowę serwisową. Umowa ma tylko jedną`GetImage`operację ( ). Ta metoda generuje mapę bitową, <xref:System.IO.MemoryStream> a następnie zapisać ją w formacie jpg. Operacja następnie zwraca ten strumień do wywołującego.  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     Zwróć uwagę na odsuwnik od drugiego do ostatniego wiersza kodu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Spowoduje to ustawienie nagłówka typu zawartości na `"image/jpeg"`. Chociaż w tym przykładzie pokazano, jak zwrócić plik jpg, można go zmodyfikować, aby zwrócić dowolny typ danych, który jest wymagany, w dowolnym formacie. Operacja musi pobrać lub wygenerować dane, a następnie zapisać je do strumienia.  
  
### <a name="to-host-the-service"></a>Aby hostować usługę  
  
1. Utwórz aplikację konsoli do obsługi usługi.  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. Utwórz zmienną do przechowywania adresu podstawowego usługi w ramach `Main` metody.  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie usługi określające klasę usługi i adres podstawowy.  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Dodaj punkt końcowy <xref:System.ServiceModel.WebHttpBinding> za <xref:System.ServiceModel.Description.WebHttpBehavior>pomocą i .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otwórz hosta usługi.  
  
    ```csharp  
    host.Open();  
    ```  
  
6. Poczekaj, aż użytkownik naciśnie klawisz ENTER, aby zakończyć działanie usługi.  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Aby wywołać usługę nieprzetworzoną przy użyciu programu Internet Explorer  
  
1. Uruchom usługę, powinny zostać wyświetlene następujące dane wyjściowe z usługi. `Service is running Press ENTER to close the host`  
  
2. Otwórz program Internet `http://localhost:8000/Service/GetImage?width=50&height=40` Explorer i wpisz żółty prostokąt z niebieską ukośną linią przez środek.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kodu dla tego tematu.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Podczas kompilowania przykładowego kodu odwołania System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
