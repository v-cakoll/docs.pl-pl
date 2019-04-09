---
title: 'Instrukcje: tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania internetowego protokołu HTTP w programie WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: f5735f4d596e17afc32b1419e9f41fd8a56af410
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157486"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Instrukcje: tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania internetowego protokołu HTTP w programie WCF
Czasami deweloperzy muszą mieć pełną kontrolę nad jak dane są zwracane z operacji usługi. Dotyczy to sytuacji, gdy operacja usługi musi zwrócić dane w formacie nie jest obsługiwane przez architekturę WCF. W tym temacie omówiono tworzenie takiej usługi przy użyciu programu WCF WEB HTTP modelu programowania. Ta usługa ma jedną operację, która zwraca strumienia.  
  
### <a name="to-implement-the-service-contract"></a>Aby zaimplementować kontrakt usługi  
  
1.  Definiowanie kontraktu usługi. Kontrakt jest nazywany `IImageServer` i jedną metodę o nazwie `GetImage` zwracającego <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Ponieważ metoda ta zwraca <xref:System.IO.Stream>, WCF przyjęto założenie, że operacja ma pełną kontrolę nad bajtów, które są zwracane z operacji usługi i są one stosowane do danych, który jest zwracany bez formatowania.  
  
2.  Implementowanie kontraktu usługi. Kontrakt ma tylko jedną operację (`GetImage`). Ta metoda generuje mapę bitową, a następnie zapisać go w celu <xref:System.IO.MemoryStream> w formacie jpg. Następnie operacja zwraca strumieniu do obiektu wywołującego.  
  
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
  
     Zwróć uwagę, druga do ostatni wiersz kodu: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     To ustawia dla nagłówka typu zawartości `"image/jpeg"`. Mimo że w tym przykładzie przedstawiono sposób zwracania plik jpg, można modyfikować do zwracania dowolnego typu danych, który jest wymagany, w dowolnym formacie. Operacja musi pobrać lub generowanie danych i następnie zapisać go w strumieniu.  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Utwórz aplikację konsolową, do obsługi usługi.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  Utwórz zmienną do przechowywania adres podstawowy dla usługi w ramach `Main` metody.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie usługi, określanie klasy usługi i adres podstawowy.  
  
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
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Aby wywołać pierwotne usługę za pomocą programu Internet Explorer  
  
1.  Uruchom usługę, powinny być widoczne następujące dane wyjściowe z usługi. `Service is running Press ENTER to close the host`  
  
2.  Otwórz program Internet Explorer i wpisz `http://localhost:8000/Service/GetImage?width=50&height=40` powinna zostać wyświetlona żółta prostokąt z niebieska linia skos, za pośrednictwem Centrum.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono pełną listę kodów w tym temacie.  
  
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
  
-   Podczas kompilowania kodu przykładowej odniesienia System.ServiceModel.dll i System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
