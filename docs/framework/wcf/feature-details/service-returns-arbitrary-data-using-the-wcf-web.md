---
title: "Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e1d808d4daf91b5ff89b05cab8359c90090f293
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF
Czasami deweloperzy musi mieć pełną kontrolę nad jak dane są zwracane z operacji usługi. Dotyczy to sytuacji, gdy operacji usługi musi zwrócić dane w formacie nie jest obsługiwana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. W tym temacie omówiono przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania pakietu sieci WEB HTTP do tworzenia takiej usługi. Ta usługa ma jedną operację, która zwraca strumienia.  
  
### <a name="to-implement-the-service-contract"></a>Aby zaimplementować kontrakt usługi  
  
1.  Definiowanie kontraktu usługi. Kontrakt jest nazywany `IImageServer` i jedną metodę o nazwie `GetImage` zwracającą <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Ponieważ metoda zwraca <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] założono, że operacja ma pełną kontrolę nad bajtów, które zostaną zwrócone z operacji usługi i dotyczy bez formatowania danych, która jest zwracana.  
  
2.  Implementowanie kontraktu usługi. Kontrakt ma tylko jedną operację (`GetImage`). Ta metoda generuje mapę bitową, a następnie zapisz go na <xref:System.IO.MemoryStream> w formacie jpg. Następnie operacja zwraca strumieniu do obiektu wywołującego.  
  
    ```  
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
  
     Zwróć uwagę drugiego do ostatniego wiersza kodu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     To ustawienie nagłówek typu zawartości `"image/jpeg"`. Chociaż ten przykład przedstawia sposób zwrócenia pliku jpg, może być modyfikowany do zwrócenia dowolnego typu danych, który jest wymagany, w dowolnym formacie. Operacja musi pobrać lub wygenerowane dane i zapisać go do strumienia.  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Utwórz aplikację konsoli do obsługi usługi.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  Utwórz zmienną do przechowywania adres podstawowy usługi w ramach `Main` metody.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienia klasy usługi i adres podstawowy usługi.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  Dodawanie punktu końcowego za pomocą <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Otworzyć hosta usługi.  
  
    ```  
    host.Open()  
    ```  
  
6.  Poczekaj, aż użytkownik naciśnie klawisz ENTER, aby zakończyć usługi.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Do wywołania tej usługi pierwotnych przy użyciu programu Internet Explorer  
  
1.  Uruchom usługę, powinny zostać wyświetlone następujące dane wyjściowe z usługi. `Service is running Press ENTER to close the host`  
  
2.  Otwórz program Internet Explorer, a następnie wpisz w `http://localhost:8000/Service/GetImage?width=50&height=40` powinna zostać wyświetlona żółta prostokąt z niebieskim linii ukośnych za pomocą Centrum.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kod w tym temacie.  
  
```  
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
  
-   W przypadku kompilowania kodu próbki kodu odwołania System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
