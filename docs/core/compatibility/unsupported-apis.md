---
title: Nieobsługiwane interfejsy API w programie .NET Core
description: Dowiedz się, które interfejsy API z .NET Framework, które zawsze zgłaszają wyjątek na platformie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 0cb533f10d53fd3d287265032e3de13c242a8ae0
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901496"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="24d80-103">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="24d80-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="24d80-104">Następujące interfejsy API będą zawsze za pomocą <xref:System.PlatformNotSupportedException> podczas uruchamiania programu .NET Core na określonej platformie.</span><span class="sxs-lookup"><span data-stu-id="24d80-104">The following APIs will always through a <xref:System.PlatformNotSupportedException> when run on .NET Core on the specified platform.</span></span>

<span data-ttu-id="24d80-105">Ten artykuł organizuje elementy członkowskie interfejsu API według przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24d80-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="24d80-106">Ten artykuł jest pracą w toku.</span><span class="sxs-lookup"><span data-stu-id="24d80-106">This article is a work-in-progress.</span></span> <span data-ttu-id="24d80-107">Nie jest to kompletna lista interfejsów API, które generują wyjątki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24d80-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="24d80-108">Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, która zgłasza na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="24d80-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="24d80-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="24d80-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="24d80-110">System</span><span class="sxs-lookup"><span data-stu-id="24d80-110">System</span></span>

| <span data-ttu-id="24d80-111">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-111">Member</span></span> | <span data-ttu-id="24d80-112">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-112">Platform</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-113">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="24d80-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="24d80-115">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="24d80-116">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-117">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="24d80-118">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="24d80-119">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="24d80-120">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-121">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="24d80-122">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="24d80-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="24d80-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="24d80-124">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-124">Member</span></span> | <span data-ttu-id="24d80-125">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-125">Platform</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-126">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-127">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-128">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="24d80-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="24d80-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="24d80-130">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-130">Member</span></span> | <span data-ttu-id="24d80-131">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-131">Platform</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-132">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-133">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="24d80-134">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="24d80-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="24d80-135">System.Configuration</span></span>

| <span data-ttu-id="24d80-136">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-136">Member</span></span> | <span data-ttu-id="24d80-137">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-137">Platform</span></span> |
| - | - |
| <span data-ttu-id="24d80-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="24d80-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="24d80-139">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="24d80-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="24d80-140">System.Console</span></span>

| <span data-ttu-id="24d80-141">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-141">Member</span></span> | <span data-ttu-id="24d80-142">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-142">Platform</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="24d80-143">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-143">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-145">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-145">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-147">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-147">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-149">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-149">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="24d80-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="24d80-151">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-152">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-153">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-154">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-154">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-155"><xref:System.Console.Title?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="24d80-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="24d80-156">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-156">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-158">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-158">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-160">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-160">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-162">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-162">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-164">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="24d80-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="24d80-165">System.Data.Common</span></span>

| <span data-ttu-id="24d80-166">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-166">Member</span></span> | <span data-ttu-id="24d80-167">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-167">Platform</span></span> |
| - | - |
| <span data-ttu-id="24d80-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (zgłasza <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="24d80-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="24d80-169">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="24d80-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="24d80-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="24d80-171">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-171">Member</span></span> | <span data-ttu-id="24d80-172">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-172">Platform</span></span> |
| - | - |
| <span data-ttu-id="24d80-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-174">Linux</span><span class="sxs-lookup"><span data-stu-id="24d80-174">Linux</span></span> |
| <span data-ttu-id="24d80-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-176">Linux</span><span class="sxs-lookup"><span data-stu-id="24d80-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="24d80-177">macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="24d80-178">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-179">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="24d80-180">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="24d80-181">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="24d80-182">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="24d80-183">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-183">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-185">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-185">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="24d80-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="24d80-187">macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-187">macOS</span></span> |
| <span data-ttu-id="24d80-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-189">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="24d80-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="24d80-190">System.IO</span></span>

| <span data-ttu-id="24d80-191">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-191">Member</span></span> | <span data-ttu-id="24d80-192">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-192">Platform</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-193">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-194">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="24d80-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="24d80-195">System.IO.Pipes</span></span>

| <span data-ttu-id="24d80-196">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-196">Member</span></span> | <span data-ttu-id="24d80-197">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-197">Platform</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="24d80-198">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="24d80-199">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="24d80-200">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="24d80-201">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-201">Linux and macOS</span></span> |
| <span data-ttu-id="24d80-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-203">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="24d80-204">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="24d80-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="24d80-205">System.Media</span></span>

| <span data-ttu-id="24d80-206">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-206">Member</span></span> | <span data-ttu-id="24d80-207">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-207">Platform</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-208">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="24d80-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="24d80-209">System.Net</span></span>

| <span data-ttu-id="24d80-210">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-210">Member</span></span> | <span data-ttu-id="24d80-211">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-211">Platform</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="24d80-212">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="24d80-213">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-214">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-215">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-216">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-217">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-218">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-219">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-220">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-221">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-222">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="24d80-223">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-224">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-225">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-226">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-227">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-228">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="24d80-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="24d80-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="24d80-230">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-230">Member</span></span> | <span data-ttu-id="24d80-231">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-231">Platform</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-232">Windows (platforma UWP)</span><span class="sxs-lookup"><span data-stu-id="24d80-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="24d80-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="24d80-233">System.Net.Sockets</span></span>

| <span data-ttu-id="24d80-234">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-234">Member</span></span> | <span data-ttu-id="24d80-235">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-235">Platform</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="24d80-236">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="24d80-237">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="24d80-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="24d80-238">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-238">Member</span></span> | <span data-ttu-id="24d80-239">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-239">Platform</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="24d80-240">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="24d80-241">System. odbicie</span><span class="sxs-lookup"><span data-stu-id="24d80-241">System.Reflection</span></span>

| <span data-ttu-id="24d80-242">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-242">Member</span></span> | <span data-ttu-id="24d80-243">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-243">Platform</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-244">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-245">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-246">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="24d80-247">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-248">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-249">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="24d80-250">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="24d80-251">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="24d80-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="24d80-252">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-252">Member</span></span> | <span data-ttu-id="24d80-253">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-253">Platform</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="24d80-254">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="24d80-255">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="24d80-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="24d80-256">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-256">Member</span></span> | <span data-ttu-id="24d80-257">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-257">Platform</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="24d80-258">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="24d80-259">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="24d80-260">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="24d80-261">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-262">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="24d80-263">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="24d80-264">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="24d80-265">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="24d80-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="24d80-266">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-266">Member</span></span> | <span data-ttu-id="24d80-267">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-267">Platform</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="24d80-268">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="24d80-269">System. Security</span><span class="sxs-lookup"><span data-stu-id="24d80-269">System.Security</span></span>

| <span data-ttu-id="24d80-270">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-270">Member</span></span> | <span data-ttu-id="24d80-271">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-271">Platform</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="24d80-272">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="24d80-273">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-274">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="24d80-275">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="24d80-276">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="24d80-277">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="24d80-278">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="24d80-279">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="24d80-280">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="24d80-281">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="24d80-282">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="24d80-283">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="24d80-284">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="24d80-285">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="24d80-286">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="24d80-286">System.Security.Claims</span></span>

| <span data-ttu-id="24d80-287">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-287">Member</span></span> | <span data-ttu-id="24d80-288">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-288">Platform</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="24d80-289">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-290">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="24d80-291">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-292">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-293">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="24d80-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="24d80-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="24d80-295">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-295">Member</span></span> | <span data-ttu-id="24d80-296">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-296">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-297">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-298">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="24d80-299">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="24d80-300">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="24d80-301">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="24d80-302">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="24d80-303">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="24d80-304">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="24d80-305">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="24d80-306">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="24d80-307">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="24d80-308">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="24d80-309">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="24d80-310">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="24d80-311">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-312">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="24d80-313">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-314">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-315">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-316">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-317">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="24d80-318">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-319">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-320">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-321">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="24d80-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-322">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-323">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="24d80-324">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="24d80-325">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="24d80-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="24d80-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="24d80-327">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-327">Member</span></span> | <span data-ttu-id="24d80-328">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-328">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="24d80-329">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="24d80-330">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="24d80-331">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="24d80-332">System. Security. Cryptography. x509</span><span class="sxs-lookup"><span data-stu-id="24d80-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="24d80-333">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-333">Member</span></span> | <span data-ttu-id="24d80-334">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-334">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-335">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-336">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-337">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-337">All</span></span> |
| <span data-ttu-id="24d80-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="24d80-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="24d80-339">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="24d80-340">System. Security. Authentication. Kiedy</span><span class="sxs-lookup"><span data-stu-id="24d80-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="24d80-341">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-341">Member</span></span> | <span data-ttu-id="24d80-342">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-342">Platform</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-343">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="24d80-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="24d80-344">System.Security.Policy</span></span>

| <span data-ttu-id="24d80-345">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-345">Member</span></span> | <span data-ttu-id="24d80-346">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-346">Platform</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-347">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="24d80-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="24d80-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="24d80-349">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-349">Member</span></span> | <span data-ttu-id="24d80-350">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-350">Platform</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-351">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="24d80-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="24d80-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="24d80-353">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-353">Member</span></span> | <span data-ttu-id="24d80-354">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-354">Platform</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-355">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="24d80-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="24d80-356">System.Threading</span></span>

| <span data-ttu-id="24d80-357">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-357">Member</span></span> | <span data-ttu-id="24d80-358">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-358">Platform</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-359">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="24d80-360">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="24d80-361">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="24d80-362">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="24d80-363">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="24d80-364">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="24d80-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="24d80-365">System.Xml</span></span>

| <span data-ttu-id="24d80-366">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24d80-366">Member</span></span> | <span data-ttu-id="24d80-367">Platforma</span><span class="sxs-lookup"><span data-stu-id="24d80-367">Platform</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="24d80-368">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="24d80-369">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="24d80-370">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="24d80-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="24d80-371">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24d80-371">See also</span></span>

- [<span data-ttu-id="24d80-372">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="24d80-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="24d80-373">Serializacja binarna w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="24d80-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="24d80-374">Analizator przenośności platformy .NET</span><span class="sxs-lookup"><span data-stu-id="24d80-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
