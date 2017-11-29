---
title: "Obsługa wielu powiązań witryny usług IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ebe433d1c18d46e0868f9566a273124e6bd63f1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a>Obsługa wielu powiązań witryny usług IIS
Odnośnie do hostowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi w obszarze Internet informacji Services (IIS) 7.0, może zajść potrzeba zapewniają wiele adres podstawowy, które używają tego samego protokołu na tej samej lokacji. Dzięki tej samej usługi odpowiedzieć na szereg różnych identyfikatorów URI. Jest to przydatne, jeśli chcesz obsługiwać usługę, która nasłuchuje http://www.contoso.com i http://contoso.com. Warto również utworzyć usługę, która ma adres podstawowy dla użytkowników wewnętrznych i oddzielne adres podstawowy dla użytkowników zewnętrznych. Na przykład: http://internal.contoso.com i http://www.contoso.com.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko przy użyciu protokołu HTTP.  
  
## <a name="multiple-base-addresses"></a>Wiele adresów bazowych  
 Ta funkcja jest dostępna jedynie dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług hostowanych w środowisku usług IIS. Ta funkcja nie jest włączona domyślnie. Aby ją włączyć, należy dodać `multipleSiteBindingsEnabled` atrybutu <`serviceHostingEnvironment`> elementu w pliku Web.config pliku i ustaw ją na `true`, jak pokazano w poniższym przykładzie.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Odnośnie do hostowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi w ramach usług IIS, usługi IIS tworzy jeden adres podstawowy, na podstawie identyfikatora URI do katalogu wirtualnego, który zawiera aplikację. Możesz dodać dodatkowe adresy podstawowy, które używają tego samego protokołu za pomocą Menedżera internetowych usług informacyjnych dodać co najmniej jednego powiązania do witryny sieci Web. Dla każdego powiązania określić protokół (HTTP lub HTTPS), adres IP, portu i nazwy hosta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]za pomocą Menedżera internetowych usług informacyjnych, zobacz [Menedżera internetowych usług informacyjnych (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Dodanie wiązań do lokacji, zobacz [utworzyć witrynę sieci Web (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 Określanie wielu adresów bazowych zawartość ma wpływ na tej samej lokacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] strona pomocy, importowanie schematu i informacji WSDL/MEX wygenerowanej przez usługę. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Strona pomocy wyświetla wiersz polecenia używany do generowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który może komunikować się z usługą. Ten wiersz polecenia zawiera tylko pierwszy adres określony w powiązaniu usługi IIS dla witryny sieci Web. Podobnie podczas importowania schematu, tylko adres podstawowy pierwszego określony w powiązaniu usług IIS jest używana. Dane WSDL oraz MEX zawierać adres podstawowy określony w powiązania usługi IIS.  
  
> [!WARNING]
>  Oznacza to, że jeśli usługa ma dwa adresy podstawowy, jeden dla użytkowników wewnętrznych i jeden dla użytkowników zewnętrznych, są określone w informacji WSDL/MEX wygenerowanej przez usługę.
