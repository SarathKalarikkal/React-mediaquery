import { useMediaQuery } from "react-responsive";

const App = () => {
  const [sidebarOpen, setSidebarOpen] = useState<boolean>(false);

  const isDesktop = useMediaQuery({ minWidth: 1024 });
  const isTablet = useMediaQuery({ minWidth: 768, maxWidth: 1023 });
  const isMobile = useMediaQuery({ maxWidth: 767 });

  const toggleSidebar = () => {
    setSidebarOpen(!sidebarOpen);
  };

  return (
    <div className="dashboard">
      {isDesktop && <Sidebar />}
      {isTablet && <Sidebar />}
      {isMobile && sidebarOpen && <Sidebar mobile onClose={toggleSidebar} />}

      <div className="main-content">
        <Header toggleSidebar={toggleSidebar} isMobile={isMobile} />
        <Content isMobile={isMobile}/>
      </div>
    </div>
  );
};

export default App;# React-mediaquery
