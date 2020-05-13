---
title: <xmlSerializer>, element
description: <xmlSerializer>Element określa, czy jest wykonywane dodatkowe sprawdzanie postępu elementu XmlSerializer.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 68037959893ec307a896ea86d21e40a9d7aa824c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380022"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="d6373-103">\<Element XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="d6373-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="d6373-104">Określa, czy dodatkowe wyboru postęp <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="d6373-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="d6373-105">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d6373-105">\<configuration></span></span>  
<span data-ttu-id="d6373-106">\<> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="d6373-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6373-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6373-107">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6373-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d6373-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d6373-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d6373-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6373-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d6373-110">Attributes</span></span>  
  
|<span data-ttu-id="d6373-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d6373-111">Attribute</span></span>|<span data-ttu-id="d6373-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d6373-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6373-113">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="d6373-113">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="d6373-114">Określa, czy postęp <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="d6373-114">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="d6373-115">Atrybut "prawda" lub "false".</span><span class="sxs-lookup"><span data-stu-id="d6373-115">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="d6373-116">Wartość domyślna to "true".</span><span class="sxs-lookup"><span data-stu-id="d6373-116">The default is "true".</span></span>|  
|<span data-ttu-id="d6373-117">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="d6373-117">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="d6373-118">Określa, czy <xref:System.Xml.Serialization.XmlSerializer> używa Generowanie starszego serializacji, generująca zestawy zapis do PLiku kodu C# i zestawiania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d6373-118">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="d6373-119">Wartość domyślna to **false**.</span><span class="sxs-lookup"><span data-stu-id="d6373-119">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6373-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d6373-120">Child Elements</span></span>  
 <span data-ttu-id="d6373-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="d6373-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6373-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d6373-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d6373-123">Element</span><span class="sxs-lookup"><span data-stu-id="d6373-123">Element</span></span>|<span data-ttu-id="d6373-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d6373-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6373-125">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="d6373-125">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="d6373-126">Zawiera ustawienia konfiguracji dla <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.</span><span class="sxs-lookup"><span data-stu-id="d6373-126">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6373-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6373-127">Remarks</span></span>  
 <span data-ttu-id="d6373-128">Domyślnie <xref:System.Xml.Serialization.XmlSerializer> zapewnia dodatkową warstwę zabezpieczeń przed potencjalnym atakom typu odmowa usługi podczas deserializacji niezaufanych danych.</span><span class="sxs-lookup"><span data-stu-id="d6373-128">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="d6373-129">Robi to za pomocą próby wykrycia podczas deserializacji w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="d6373-129">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="d6373-130">W przypadku wykrycia takiego warunku zostanie zgłoszony wyjątek z następującym komunikatem: "błąd wewnętrzny: deserializacja nie powiodła się przed strumieniem bazowym".</span><span class="sxs-lookup"><span data-stu-id="d6373-130">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="d6373-131">Odbieranie ten komunikat nie musi oznaczać, że typu "odmowa usługi" jest w toku.</span><span class="sxs-lookup"><span data-stu-id="d6373-131">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="d6373-132">W niektórych sytuacjach szczególnych mechanizm wykrywania pętli nieskończonej tworzy fałszywego ostrzeżenia i wyjątku wiarygodnego wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="d6373-132">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="d6373-133">Jeśli okaże się, że w konkretnej aplikacji legalne komunikaty są odrzucane przez tę dodatkową warstwę ochrony, ustaw atrybut **checkDeserializeAdvances** na wartość "false".</span><span class="sxs-lookup"><span data-stu-id="d6373-133">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6373-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6373-134">Example</span></span>  
 <span data-ttu-id="d6373-135">Poniższy przykład kodu ustawia atrybut **checkDeserializeAdvances** na wartość "false".</span><span class="sxs-lookup"><span data-stu-id="d6373-135">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6373-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6373-136">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="d6373-137">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="d6373-137">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="d6373-138">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="d6373-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
