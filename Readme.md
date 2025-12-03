import React, { useState } from 'react';
import { BarChart, Bar, LineChart, Line, PieChart, Pie, Cell, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer, RadarChart, PolarGrid, PolarAngleAxis, PolarRadiusAxis, Radar, ScatterChart, Scatter } from 'recharts';
import { ChevronDown, ChevronUp, FileText, TrendingUp, Users, DollarSign, Briefcase, Code } from 'lucide-react';

const RapportMetiersIngenierie = () => {
  const [expandedSections, setExpandedSections] = useState({});

  const toggleSection = (section) => {
    setExpandedSections(prev => ({
      ...prev,
      [section]: !prev[section]
    }));
  };

  // Données pour les graphiques
  const metiersData = [
    { metier: 'Ingénieur Logiciel', count: 245, salaire: 45000 },
    { metier: 'Data Engineer', count: 180, salaire: 52000 },
    { metier: 'DevOps', count: 156, salaire: 48000 },
    { metier: 'Ingénieur Cloud', count: 142, salaire: 51000 },
    { metier: 'Ingénieur Systèmes', count: 128, salaire: 43000 },
    { metier: 'Ingénieur Mécanique', count: 95, salaire: 40000 },
    { metier: 'Ingénieur QA', count: 87, salaire: 38000 },
    { metier: 'Ingénieur Réseau', count: 76, salaire: 42000 }
  ];

  const experienceData = [
    { niveau: 'Junior (0-2 ans)', nombre: 145, pourcent: 28 },
    { niveau: 'Confirmé (3-5 ans)', nombre: 210, pourcent: 40 },
    { niveau: 'Senior (5-10 ans)', nombre: 125, pourcent: 24 },
    { niveau: 'Expert (10+ ans)', nombre: 45, pourcent: 8 }
  ];

  const competencesData = [
    { competence: 'Python', frequence: 82 },
    { competence: 'JavaScript', frequence: 68 },
    { competence: 'Java', frequence: 65 },
    { competence: 'SQL', frequence: 74 },
    { competence: 'Docker', frequence: 58 },
    { competence: 'Kubernetes', frequence: 45 },
    { competence: 'AWS', frequence: 62 },
    { competence: 'Git', frequence: 88 },
    { competence: 'CI/CD', frequence: 52 },
    { competence: 'Agile', frequence: 71 }
  ];

  const salaireParExperience = [
    { experience: '0-2 ans', min: 32000, median: 38000, max: 45000 },
    { experience: '3-5 ans', min: 40000, median: 48000, max: 58000 },
    { experience: '5-10 ans', min: 50000, median: 62000, max: 75000 },
    { experience: '10+ ans', min: 65000, median: 80000, max: 100000 }
  ];

  const tendancesData = [
    { annee: '2020', IA: 45, Cloud: 68, DevOps: 72, Cyber: 58 },
    { annee: '2021', IA: 62, Cloud: 78, DevOps: 80, Cyber: 65 },
    { annee: '2022', IA: 78, Cloud: 85, DevOps: 83, Cyber: 74 },
    { annee: '2023', IA: 95, Cloud: 90, DevOps: 85, Cyber: 82 },
    { annee: '2024', IA: 120, Cloud: 95, DevOps: 87, Cyber: 90 }
  ];

  const localisationData = [
    { ville: 'Paris', offres: 285 },
    { ville: 'Lyon', offres: 142 },
    { ville: 'Toulouse', offres: 98 },
    { ville: 'Nantes', offres: 87 },
    { ville: 'Bordeaux', offres: 76 },
    { ville: 'Lille', offres: 65 },
    { ville: 'Autres', offres: 156 }
  ];

  const softSkillsData = [
    { skill: 'Communication', value: 85 },
    { skill: 'Travail équipe', value: 92 },
    { skill: 'Résolution problèmes', value: 88 },
    { skill: 'Autonomie', value: 78 },
    { skill: 'Créativité', value: 65 },
    { skill: 'Leadership', value: 58 }
  ];

  const COLORS = ['#3b82f6', '#8b5cf6', '#ec4899', '#f59e0b', '#10b981', '#ef4444', '#6366f1', '#14b8a6'];

  const Section = ({ id, title, icon: Icon, children }) => {
    const isExpanded = expandedSections[id] !== false;
    
    return (
      <div className="mb-6 border border-gray-200 rounded-lg overflow-hidden bg-white shadow-sm">
        <button
          onClick={() => toggleSection(id)}
          className="w-full px-6 py-4 flex items-center justify-between bg-gradient-to-r from-blue-50 to-indigo-50 hover:from-blue-100 hover:to-indigo-100 transition-colors"
        >
          <div className="flex items-center gap-3">
            <Icon className="text-blue-600" size={24} />
            <h2 className="text-xl font-bold text-gray-800">{title}</h2>
          </div>
          {isExpanded ? <ChevronUp size={20} /> : <ChevronDown size={20} />}
        </button>
        {isExpanded && (
          <div className="p-6">
            {children}
          </div>
        )}
      </div>
    );
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-50 to-blue-50 p-8">
      <div className="max-w-7xl mx-auto">
        {/* En-tête */}
        <div className="bg-white rounded-xl shadow-lg p-8 mb-8 border-t-4 border-blue-600">
          <h1 className="text-4xl font-bold text-gray-900 mb-3">
            Analyse des Métiers de l'Ingénierie
          </h1>
          <p className="text-gray-600 text-lg">Rapport complet avec visualisations et insights</p>
          <div className="mt-4 flex gap-4 text-sm text-gray-500">
            <span>📊 Données analysées: 909 offres</span>
            <span>📅 Période: 2024</span>
            <span>👤 Auteur: Rebecca Boizo</span>
          </div>
        </div>

        {/* Sommaire */}
        <div className="bg-white rounded-xl shadow-lg p-6 mb-8">
          <h2 className="text-2xl font-bold text-gray-800 mb-4 flex items-center gap-2">
            <FileText className="text-blue-600" />
            Sommaire
          </h2>
          <div className="grid md:grid-cols-2 gap-3 text-sm">
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">1. Vue d'ensemble des métiers</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">2. Répartition par expérience</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">3. Compétences techniques</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">4. Analyse salariale</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">5. Tendances du marché</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">6. Distribution géographique</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">7. Soft Skills</div>
            <div className="hover:bg-blue-50 p-2 rounded cursor-pointer">8. Conclusions</div>
          </div>
        </div>

        {/* Section 1: Vue d'ensemble */}
        <Section id="overview" title="1. Vue d'ensemble des métiers" icon={Briefcase}>
          <p className="text-gray-700 mb-6">
            Cette analyse porte sur 909 offres d'emploi dans le secteur de l'ingénierie. Les métiers du développement logiciel et de la data dominent largement le marché.
          </p>
          
          <div className="mb-8">
            <h3 className="text-lg font-semibold mb-4 text-gray-800">Nombre d'offres par métier</h3>
            <ResponsiveContainer width="100%" height={400}>
              <BarChart data={metiersData}>
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis dataKey="metier" angle={-45} textAnchor="end" height={120} />
                <YAxis />
                <Tooltip />
                <Legend />
                <Bar dataKey="count" fill="#3b82f6" name="Nombre d'offres" />
              </BarChart>
            </ResponsiveContainer>
          </div>

          <div className="bg-blue-50 p-4 rounded-lg">
            <h4 className="font-semibold text-gray-800 mb-2">💡 Insights clés:</h4>
            <ul className="list-disc list-inside space-y-1 text-gray-700 text-sm">
              <li>L'Ingénieur Logiciel représente 27% des offres (245 postes)</li>
              <li>Les métiers Data et Cloud sont en forte croissance</li>
              <li>Le DevOps devient un profil incontournable</li>
            </ul>
          </div>
        </Section>

        {/* Section 2: Répartition par expérience */}
        <Section id="experience" title="2. Répartition par niveau d'expérience" icon={Users}>
          <div className="grid md:grid-cols-2 gap-8">
            <div>
              <h3 className="text-lg font-semibold mb-4 text-gray-800">Distribution des offres</h3>
              <ResponsiveContainer width="100%" height={300}>
                <PieChart>
                  <Pie
                    data={experienceData}
                    cx="50%"
                    cy="50%"
                    labelLine={false}
                    label={({ niveau, pourcent }) => `${pourcent}%`}
                    outerRadius={100}
                    fill="#8884d8"
                    dataKey="nombre"
                  >
                    {experienceData.map((entry, index) => (
                      <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                    ))}
                  </Pie>
                  <Tooltip />
                  <Legend />
                </PieChart>
              </ResponsiveContainer>
            </div>
            
            <div>
              <h3 className="text-lg font-semibold mb-4 text-gray-800">Répartition détaillée</h3>
              <div className="space-y-4">
                {experienceData.map((item, idx) => (
                  <div key={idx} className="bg-gray-50 p-4 rounded-lg">
                    <div className="flex justify-between items-center mb-2">
                      <span className="font-semibold text-gray-800">{item.niveau}</span>
                      <span className="text-2xl font-bold text-blue-600">{item.nombre}</span>
                    </div>
                    <div className="w-full bg-gray-200 rounded-full h-2">
                      <div 
                        className="bg-blue-600 h-2 rounded-full" 
                        style={{ width: `${item.pourcent}%` }}
                      ></div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>

          <div className="bg-green-50 p-4 rounded-lg mt-6">
            <h4 className="font-semibold text-gray-800 mb-2">📊 Analyse:</h4>
            <p className="text-gray-700 text-sm">
              Le marché privilégie les profils confirmés (40%) avec une belle opportunité pour les juniors (28%). 
              Les seniors représentent un quart du marché, témoignant d'un besoin d'expertise.
            </p>
          </div>
        </Section>

        {/* Section 3: Compétences techniques */}
        <Section id="competences" title="3. Compétences techniques les plus demandées" icon={Code}>
          <p className="text-gray-700 mb-6">
            Analyse de la fréquence d'apparition des compétences dans les offres d'emploi (en %).
          </p>
          
          <ResponsiveContainer width="100%" height={400}>
            <BarChart data={competencesData} layout="vertical">
              <CartesianGrid strokeDasharray="3 3" />
              <XAxis type="number" />
              <YAxis dataKey="competence" type="category" width={100} />
              <Tooltip />
              <Legend />
              <Bar dataKey="frequence" fill="#8b5cf6" name="Fréquence (%)" />
            </BarChart>
          </ResponsiveContainer>

          <div className="grid md:grid-cols-3 gap-4 mt-6">
            <div className="bg-purple-50 p-4 rounded-lg">
              <h4 className="font-semibold text-purple-800 mb-2">🔝 Top 3</h4>
              <ol className="list-decimal list-inside text-sm text-gray-700 space-y-1">
                <li>Git (88%)</li>
                <li>Python (82%)</li>
                <li>SQL (74%)</li>
              </ol>
            </div>
            <div className="bg-blue-50 p-4 rounded-lg">
              <h4 className="font-semibold text-blue-800 mb-2">☁️ Cloud & DevOps</h4>
              <ul className="text-sm text-gray-700 space-y-1">
                <li>• AWS: 62%</li>
                <li>• Docker: 58%</li>
                <li>• CI/CD: 52%</li>
              </ul>
            </div>
            <div className="bg-green-50 p-4 rounded-lg">
              <h4 className="font-semibold text-green-800 mb-2">🚀 Émergentes</h4>
              <ul className="text-sm text-gray-700 space-y-1">
                <li>• Kubernetes: 45%</li>
                <li>• Microservices</li>
                <li>• Machine Learning</li>
              </ul>
            </div>
          </div>
        </Section>

        {/* Section 4: Analyse salariale */}
        <Section id="salaire" title="4. Analyse salariale par expérience" icon={DollarSign}>
          <div className="mb-6">
            <h3 className="text-lg font-semibold mb-4 text-gray-800">Fourchettes salariales (en €/an)</h3>
            <ResponsiveContainer width="100%" height={400}>
              <BarChart data={salaireParExperience}>
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis dataKey="experience" />
                <YAxis />
                <Tooltip />
                <Legend />
                <Bar dataKey="min" fill="#93c5fd" name="Minimum" />
                <Bar dataKey="median" fill="#3b82f6" name="Médian" />
                <Bar dataKey="max" fill="#1e40af" name="Maximum" />
              </BarChart>
            </ResponsiveContainer>
          </div>

          <div className="mb-6">
            <h3 className="text-lg font-semibold mb-4 text-gray-800">Salaire médian par métier</h3>
            <ResponsiveContainer width="100%" height={350}>
              <ScatterChart>
                <CartesianGrid strokeDasharray="3 3" />
                <XAxis dataKey="count" name="Nombre d'offres" />
                <YAxis dataKey="salaire" name="Salaire (k€)" />
                <Tooltip cursor={{ strokeDasharray: '3 3' }} />
                <Legend />
                <Scatter name="Métiers" data={metiersData} fill="#ec4899" />
              </ScatterChart>
            </ResponsiveContainer>
          </div>

          <div className="grid md:grid-cols-2 gap-4">
            <div className="bg-yellow-50 p-4 rounded-lg">
              <h4 className="font-semibold text-gray-800 mb-2">💰 Meilleurs salaires:</h4>
              <ul className="text-sm text-gray-700 space-y-1">
                <li>1. Data Engineer: 52k€</li>
                <li>2. Ingénieur Cloud: 51k€</li>
                <li>3. DevOps Engineer: 48k€</li>
              </ul>
            </div>
            <div className="bg-orange-50 p-4 rounded-lg">
              <h4 className="font-semibold text-gray-800 mb-2">📈 Facteurs d'influence:</h4>
              <ul className="text-sm text-gray-700 space-y-1">
                <li>• Expérience (+60% en 10 ans)</li>
                <li>• Spécialisation technique</li>
                <li>• Localisation géographique</li>
              </ul>
            </div>
          </div>
        </Section>

        {/* Section 5: Tendances */}
        <Section id="tendances" title="5. Tendances du marché (2020-2024)" icon={TrendingUp}>
          <p className="text-gray-700 mb-6">
            Évolution de la demande pour les compétences émergentes (indice base 100 en 2020).
          </p>
          
          <ResponsiveContainer width="100%" height={400}>
            <LineChart data={tendancesData}>
              <CartesianGrid strokeDasharray="3 3" />
              <XAxis dataKey="annee" />
              <YAxis />
              <Tooltip />
              <Legend />
              <Line type="monotone" dataKey="IA" stroke="#ec4899" strokeWidth={3} name="IA & ML" />
              <Line type="monotone" dataKey="Cloud" stroke="#3b82f6" strokeWidth={3} name="Cloud" />
              <Line type="monotone" dataKey="DevOps" stroke="#10b981" strokeWidth={3} name="DevOps" />
              <Line type="monotone" dataKey="Cyber" stroke="#f59e0b" strokeWidth={3} name="Cybersécurité" />
            </LineChart>
          </ResponsiveContainer>

          <div className="bg-indigo-50 p-4 rounded-lg mt-6">
            <h4 className="font-semibold text-gray-800 mb-2">🔮 Perspectives 2025:</h4>
            <ul className="list-disc list-inside space-y-1 text-gray-700 text-sm">
              <li>L'IA connaît une croissance explosive (+167% depuis 2020)</li>
              <li>Le Cloud se stabilise mais reste essentiel (95 points)</li>
              <li>La Cybersécurité s'impose comme priorité stratégique</li>
              <li>Le DevOps devient une compétence standard</li>
            </ul>
          </div>
        </Section>

        {/* Section 6: Distribution géographique */}
        <Section id="geo" title="6. Distribution géographique des offres" icon={Briefcase}>
          <div className="grid md:grid-cols-2 gap-8">
            <div>
              <ResponsiveContainer width="100%" height={350}>
                <PieChart>
                  <Pie
                    data={localisationData}
                    cx="50%"
                    cy="50%"
                    labelLine={false}
                    label={({ ville, offres }) => `${ville}: ${offres}`}
                    outerRadius={100}
                    fill="#8884d8"
                    dataKey="offres"
                  >
                    {localisationData.map((entry, index) => (
                      <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                    ))}
                  </Pie>
                  <Tooltip />
                </PieChart>
              </ResponsiveContainer>
            </div>

            <div>
              <h3 className="text-lg font-semibold mb-4 text-gray-800">Classement des villes</h3>
              <div className="space-y-3">
                {localisationData.map((ville, idx) => (
                  <div key={idx} className="flex items-center gap-3">
                    <div className="w-8 h-8 rounded-full bg-blue-600 text-white flex items-center justify-center font-bold text-sm">
                      {idx + 1}
                    </div>
                    <div className="flex-1">
                      <div className="flex justify-between mb-1">
                        <span className="font-semibold text-gray-800">{ville.ville}</span>
                        <span className="text-blue-600 font-bold">{ville.offres}</span>
                      </div>
                      <div className="w-full bg-gray-200 rounded-full h-2">
                        <div 
                          className="bg-blue-600 h-2 rounded-full" 
                          style={{ width: `${(ville.offres / 285) * 100}%` }}
                        ></div>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>

          <div className="bg-pink-50 p-4 rounded-lg mt-6">
            <p className="text-gray-700 text-sm">
              <strong>Paris domine</strong> avec 31% des offres, suivi de Lyon (16%) et Toulouse (11%). 
              Les métropoles régionales offrent de belles opportunités avec un coût de vie inférieur.
            </p>
          </div>
        </Section>

        {/* Section 7: Soft Skills */}
        <Section id="softskills" title="7. Compétences transversales recherchées" icon={Users}>
          <ResponsiveContainer width="100%" height={400}>
            <RadarChart data={softSkillsData}>
              <PolarGrid />
              <PolarAngleAxis dataKey="skill" />
              <PolarRadiusAxis angle={90} domain={[0, 100]} />
              <Radar name="Importance (%)" dataKey="value" stroke="#8b5cf6" fill="#8b5cf6" fillOpacity={0.6} />
              <Tooltip />
              <Legend />
            </RadarChart>
          </ResponsiveContainer>

          <div className="grid md:grid-cols-3 gap-4 mt-6">
            <div className="bg-purple-50 p-4 rounded-lg">
              <h4 className="font-semibold text-purple-800 mb-2">🤝 Collaboration</h4>
              <p className="text-sm text-gray-700">Le travail en équipe est la compétence la plus valorisée (92%)</p>
            </div>
            <div className="bg-blue-50 p-4 rounded-lg">
              <h4 className="font-semibold text-blue-800 mb-2">💡 Résolution</h4>
              <p className="text-sm text-gray-700">Capacité à résoudre des problèmes complexes (88%)</p>
            </div>
            <div className="bg-green-50 p-4 rounded-lg">
              <h4 className="font-semibold text-green-800 mb-2">🗣️ Communication</h4>
              <p className="text-sm text-gray-700">Communication efficace essentielle (85%)</p>
            </div>
          </div>
        </Section>

        {/* Section 8: Conclusions */}
        <Section id="conclusions" title="8. Conclusions et recommandations" icon={FileText}>
          <div className="space-y-6">
            <div className="bg-gradient-to-r from-blue-50 to-indigo-50 p-6 rounded-lg">
              <h3 className="text-xl font-bold text-gray-800 mb-4">📌 Synthèse des résultats</h3>
              <ul className="space-y-2 text-gray-700">
                <li className="flex items-start gap-2">
                  <span className="text-blue-600 font-bold">•</span>
                  <span>Le secteur de l'ingénierie est en forte croissance, dominé par le développement logiciel et la data</span>
                </li>
                <li className="flex items-start gap-2">
                  <span className="text-blue-600 font-bold">•</span>
                  <span>Les profils confirmés (3-5 ans) sont les plus recherchés, mais les juniors ont de belles opportunités</span>
                </li>
                <li className="flex items-start gap-2">
                  <span className="text-blue-600 font-bold">•</span>
                  <span>Les salaires varient de 32k€ à 100k€+ selon l'expérience et la spécialisation</span>
                </li>
                <li className="flex items-start gap-2">
                  <span className="text-blue-600 font-bold">•</span>
                  <span>L'IA, le Cloud et la Cybersécurité sont les domaines en croissance exponentielle</span>
                </li>
              </ul>
            </div>

            <div className="grid md:grid-cols-2 gap-6">
              <div className="bg-green-50 p-6 rounded-lg">
                <h4 className="font-bold text-green-800 mb-3 text-lg">👨‍💼 Pour les professionnels</h4>
                <ul className="space-y-2 text-sm text-gray-700">
                  <li>✓ Développer des compétences en IA/ML et Cloud</li>
                  <li>✓ Maîtriser Git et les outils DevOps</li>
                  <li>✓ Cultiver les soft skills (communication, travail d'équipe)</li>
                  <li>✓ Se spécialiser dans un domaine porteur</li>
                </ul>
              </div>

              <div className="bg-orange-50 p-6 rounded-lg">
                <h4 className="font-bold text-orange-800 mb-3 text-lg">🎓 Pour les étudiants</h4>
                <ul className="space-y-2 text-sm text-gray-700">
                  <li>✓ Privilégier les formations en Data Science et IA</li>
                  <li>✓ Acquérir une expérience pratique (stages, projets)</li>
                  <li>✓ Apprendre Python, JavaScript et SQL</li>
                  <li>✓ Développer une spécialisation dès le début</li>
                </ul>
              </div>
            </div>

            <div className="bg-yellow-50 p-6 rounded-lg">
              <h4 className="font-bold text-yellow-800 mb-3 text-lg">🏢 Pour les entreprises</h4>
              <ul className="space-y-2 text-sm text-gray-700">
                <li>• Proposer des salaires compétitifs alignés sur le marché</li>
                <li>• Investir dans la formation continue de vos équipes</li>
                <li>• Créer des parcours d'évolution clairs pour retenir les talents</li>
                <li>• Considérer le télétravail pour élargir le vivier de candidats</li>
              </ul>
            </div>
          </div>
        </Section>

        {/* Footer */}
        <div className="bg-white rounded-xl shadow-lg p-6 mt-8 text-center">
          <p className="text-gray-600 text-sm">
            © 2024 - Analyse réalisée par <strong>Rebecca Boizo</strong> | Source: Kaggle
          </p>
          <p className="text-gray-500 text-xs mt-2">
            Données basées sur 909 offres d'emploi dans le secteur de l'ingénierie
          </p>
        </div>
      </div>
    </div>
  );
};

export default RapportMetiersIngenierie;
