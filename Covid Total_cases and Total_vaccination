--Select*
--From [Portfolio Project].dbo.Covid_Death$
--where continent is not null
--order By 3,4

----select data that we are going to be started

--select location,date,total_cases,new_cases
--from [Portfolio Project].dbo.Covid_Death$
--where continent is not null
--order by 1,2

---- Total_Cases VS Total_Deaths

--select location,date,total_cases,total_deaths, (total_cases/Total_deaths)*100 As DeathPercentage
--from [Portfolio Project].dbo.Covid_Death$
--where location like '%india%'
--And continent is not null
--order by 1,2

----Total_Cases VS Population

--select location,date,total_cases,population, (total_cases/population)*100 As Percentagepopulationinfected
--from [Portfolio Project].dbo.Covid_Death$
----where location like '%india%'
--order by 1,2

----Countries with highest infected rate compared to population

--Select location,population, Max(total_cases) As Highestinfectedcount, Max((total_cases/population))*100 As Percentagepopulationinfected
--from [Portfolio Project].dbo.Covid_Death$
------where location like '%india%'
--Group by location,population
--Order by Percentagepopulationinfected DESC

----Countries with highest death count per population

--Select location, Max(cast(total_deaths as int)) As TotalDeathCount
--from [Portfolio Project].dbo.Covid_Death$
----where location like '%india%'
--where continent is not null
--Group by location
--Order by TotalDeathCount Desc

---- Lets Break Things by Continent

--Select continent, Max(cast(total_deaths as int)) As TotalDeathCount
--from [Portfolio Project].dbo.Covid_Death$
----where location like '%india%'
--where continent is not null
--Group by continent
--Order by TotalDeathCount Desc

----Continent with the highest death count per population

--Select continent, Max(cast(total_deaths as int)) As TotalDeathCount
--from [Portfolio Project].dbo.Covid_Death$
----where location like '%india%'
--where continent is not null
--Group by continent
--Order by TotalDeathCount Desc

----Global Number

--select date,sum(new_cases)as totalcases,sum(cast(new_deaths as int))as totaldeaths,sum(cast(new_deaths as int))/sum(new_cases)*100 As Deathpercentage
--from [Portfolio Project].dbo.Covid_Death$
----where location like '%india%'
--where continent is not null
--Group By date
--order by 1,2

--Total Population VS Total Vaccination

--With PopvsVac (continent,location,date,population,new_vaccinations,rollingpeoplevaccinated)
--as
--(
--select dea.continent, dea.location,dea.date,dea.population,vac.new_vaccinations
--,sum(cast(vac.new_vaccinations as int)) OVER (partition by dea.location order by dea.location
--,dea.date) as rollingpeoplevaccinated
--from [Portfolio Project].dbo.Covid_Death$ As dea
--join [Portfolio Project].dbo.Covid_vaccination$ As vac
--on dea.location = vac.location
--and dea.date = vac.date
--where dea.continent is not null
----order by 2,3
--)
--Select*,(rollingpeoplevaccinated/population)*100
--from PopvsVac

----Temp Table
--Drop Table if exists #percentpopulationvaccinated
--Create Table #percentpopulationvaccinated
--(
--continent nvarchar (255),
--location nvarchar (255),
--Date Datetime,
--Population numeric,
--new_vaccinations numeric,
--rollingpeoplevaccinated numeric,
--)

--insert into #percentpopulationvaccinated

--select dea.continent, dea.location,dea.date,dea.population,vac.new_vaccinations
--,sum(convert(bigint,vac.new_vaccinations)) OVER (partition by dea.location order by dea.location
--,dea.date) as rollingpeoplevaccinated
--from [Portfolio Project].dbo.Covid_Death$ As dea
--join [Portfolio Project].dbo.Covid_vaccination$ As vac
--on dea.location = vac.location
--and dea.date = vac.date
--where dea.continent is not null
----order by 2,3

--Select*,(rollingpeoplevaccinated/population)*100
--from #percentpopulationvaccinated

--creating View to store for later visulaizations

--create view percentpopulationvaccinated as
--select dea.continent, dea.location,dea.date,dea.population,vac.new_vaccinations
--,sum(convert(bigint,vac.new_vaccinations)) OVER (partition by dea.location order by dea.location
--,dea.date) as rollingpeoplevaccinated
--from [Portfolio Project].dbo.Covid_Death$ As dea
--join [Portfolio Project].dbo.Covid_vaccination$ As vac
--on dea.location = vac.location
--and dea.date = vac.date
--where dea.continent is not null
----order by 2,3








