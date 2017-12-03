---
title: "&lt;Element xmlSerializer&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17e4fcd1b471a5197f2e6a30bad10cbdbe22f216
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlserializergt-element"></a><span data-ttu-id="688db-102">&lt;Element xmlSerializer&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="688db-102">&lt;xmlSerializer&gt; Element</span></span>
<span data-ttu-id="688db-103">Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="688db-103">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="688db-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="688db-104">\<configuration></span></span>  
<span data-ttu-id="688db-105">\<System.XML.serialization ></span><span class="sxs-lookup"><span data-stu-id="688db-105">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="688db-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="688db-106">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true"|"false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="688db-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="688db-107">Attributes and Elements</span></span>  
 <span data-ttu-id="688db-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="688db-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="688db-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="688db-109">Attributes</span></span>  
  
|<span data-ttu-id="688db-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="688db-110">Attribute</span></span>|<span data-ttu-id="688db-111">Opis</span><span class="sxs-lookup"><span data-stu-id="688db-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="688db-112">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="688db-112">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="688db-113">Określa, czy postęp <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="688db-113">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="688db-114">Atrybut "prawda" lub "false".</span><span class="sxs-lookup"><span data-stu-id="688db-114">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="688db-115">Wartość domyślna to "true".</span><span class="sxs-lookup"><span data-stu-id="688db-115">The default is "true".</span></span>|  
|<span data-ttu-id="688db-116">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="688db-116">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="688db-117">Określa, czy <xref:System.Xml.Serialization.XmlSerializer> używa Generowanie starszego serializacji, generująca zestawy zapis do PLiku kodu C# i zestawiania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="688db-117">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="688db-118">Wartość domyślna to **false**.</span><span class="sxs-lookup"><span data-stu-id="688db-118">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="688db-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="688db-119">Child Elements</span></span>  
 <span data-ttu-id="688db-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="688db-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="688db-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="688db-121">Parent Elements</span></span>  
  
|<span data-ttu-id="688db-122">Element</span><span class="sxs-lookup"><span data-stu-id="688db-122">Element</span></span>|<span data-ttu-id="688db-123">Opis</span><span class="sxs-lookup"><span data-stu-id="688db-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="688db-124">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="688db-124">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="688db-125">Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="688db-125">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="688db-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="688db-126">Remarks</span></span>  
 <span data-ttu-id="688db-127">Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="688db-127">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="688db-128">Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="688db-128">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="688db-129">W przypadku wykrycia takim stanie, jest zwracany wyjątek z następującym komunikatem: "Błąd wewnętrzny: Deserializacja nie powiodła się z przechodzeniem do odpowiedniego strumienia do."</span><span class="sxs-lookup"><span data-stu-id="688db-129">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="688db-130">Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku.</span><span class="sxs-lookup"><span data-stu-id="688db-130">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="688db-131">W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="688db-131">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="688db-132">Jeśli okaże się, że w szczególności aplikacji istotnych wiadomości są odrzucane przez ten dodatkową warstwę ochrony, należy ustawić **checkDeserializeAdvances** atrybutu na "false".</span><span class="sxs-lookup"><span data-stu-id="688db-132">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="688db-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="688db-133">Example</span></span>  
 <span data-ttu-id="688db-134">Poniższy kod przykładzie **checkDeserializeAdvances** atrybutu na "false".</span><span class="sxs-lookup"><span data-stu-id="688db-134">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="688db-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="688db-135">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="688db-136">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="688db-136">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="688db-137">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="688db-137">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
